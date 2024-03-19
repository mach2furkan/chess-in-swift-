    # chess-in-swift-
    //
    //  main.swift
    //  chess
    //
    //  Created by Furkan Aşkın on 20.03.2024.
        //
    import Foundation

    // Define the Chessboard structure
            struct Chessboard {
    var board: [[Piece?]] = Array(repeating: Array(repeating: nil, count: 8), count: 8)
    
    init() {
        // Set up the initial board state
        initializeBoard()
    }
    
    // Function to initialize the board with pieces
    mutating func initializeBoard() {
        // Place Pawns
        for col in 0..<8 {
            board[1][col] = Piece(color: .white, type: .pawn)
            board[6][col] = Piece(color: .black, type: .pawn)
        }
        
        // Place Rooks
        board[0][0] = Piece(color: .white, type: .rook)
        board[0][7] = Piece(color: .white, type: .rook)
        board[7][0] = Piece(color: .black, type: .rook)
        board[7][7] = Piece(color: .black, type: .rook)
        
        // Place Knights
        board[0][1] = Piece(color: .white, type: .knight)
        board[0][6] = Piece(color: .white, type: .knight)
        board[7][1] = Piece(color: .black, type: .knight)
        board[7][6] = Piece(color: .black, type: .knight)
        
        // Place Bishops
        board[0][2] = Piece(color: .white, type: .bishop)
        board[0][5] = Piece(color: .white, type: .bishop)
        board[7][2] = Piece(color: .black, type: .bishop)
        board[7][5] = Piece(color: .black, type: .bishop)
        
        // Place Queens
        board[0][3] = Piece(color: .white, type: .queen)
        board[7][3] = Piece(color: .black, type: .queen)
        
        // Place Kings
        board[0][4] = Piece(color: .white, type: .king)
        board[7][4] = Piece(color: .black, type: .king)
    }
    
    // Function to print the current state of the board
    func printBoard() {
        for row in board {
            for piece in row {
                if let piece = piece {
                    print(piece.symbol, terminator: " ")
                } else {
                    print(".", terminator: " ")
                }
            }
            print()
        }
    }
    }

    // Define the Piece structure
      struct Piece {
    let color: Color
    let type: PieceType
    
    var symbol: String {
        switch (color, type) {
        case (.white, .pawn): return "♙"
        case (.white, .rook): return "♖"
        case (.white, .knight): return "♘"
        case (.white, .bishop): return "♗"
        case (.white, .queen): return "♕"
        case (.white, .king): return "♔"
        case (.black, .pawn): return "♟"
        case (.black, .rook): return "♜"
        case (.black, .knight): return "♞"
        case (.black, .bishop): return "♝"
        case (.black, .queen): return "♛"
        case (.black, .king): return "♚"
        }
    }
    }

    // Define the Color enumeration
    enum Color {
    case white
    case black
    }

      // Define the PieceType enumeration
      enum PieceType {
    case pawn
    case rook
    case knight
    case bishop
    case queen
    case king
    }

    // Main code
    var chessboard = Chessboard()
    chessboard.printBoard()
