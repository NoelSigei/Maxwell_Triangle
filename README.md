# Maxwell_Triangle
    import matplotlib.pyplot as plt
    import numpy as np
    from mpl_toolkits.mplot3d.art3d import Poly3DCollection

    def plot_maxwell_triangle():
        # RGB primary coordinates (vertices of the triangle)
        vertices = np.array([[1, 0, 0], [0, 1, 0], [0, 0, 1]])
        triangle = Poly3DCollection([vertices], alpha=0.5, edgecolors='black')
        triangle.set_facecolor([[1, 0, 0], [0, 1, 0], [0, 0, 1]])

        # Edges of the RGB cube
        edges = np.array([[1, 0, 0], [0, 1, 0], [0, 0, 1], [0, 0, 0],
                         [1, 1, 0], [1, 0, 1], [0, 1, 1], [1, 1, 1]])
    
        # Initialize 3D plot
        fig = plt.figure()
        ax = fig.add_subplot(111, projection='3d')
    
        # Draw the triangle and cube
        ax.add_collection3d(triangle)
        ax.scatter(vertices[:, 0], vertices[:, 1], vertices[:, 2], c=vertices, s=100)
        for i in range(len(edges)):
            for j in range(i + 1, len(edges)):
                ax.plot3D(*zip(edges[i], edges[j]), color="gray", linestyle="--")
    
        # Add labels and adjust limits
        ax.set_xlim([0, 1])
        ax.set_ylim([0, 1])
        ax.set_zlim([0, 1])
        ax.set_xlabel('Red')
        ax.set_ylabel('Green')
        ax.set_zlabel('Blue')
        plt.title("Maxwell Triangle in RGB Space")
        plt.show()

    plot_maxwell_triangle()
