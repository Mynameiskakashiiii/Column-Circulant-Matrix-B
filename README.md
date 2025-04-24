% Given vectors
a = [];
c = [];
n = length(c);

% Initialize column-wise circulant matrices
C = zeros(n);
A = zeros(n);

% Build C from c (each column is a right shift of the previous)
for i = 1:n
    C(:, i) = circshift(c, i - 1);
end

% Build A from a
for i = 1:n
    A(:, i) = circshift(a, i - 1);
end

% Transpose A
AT = A';

% Check invertibility
if rank(AT) < n
    error('Matrix A^T is not invertible!');
end

% Solve for B
B = AT\C;

% Display results
disp('Matrix C:');
disp(C);

disp('Matrix A:');
disp(A);

disp('Solution B');
disp(B);
