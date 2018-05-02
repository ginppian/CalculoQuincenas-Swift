Calculo de quincenas
===

* Con la siguiente función calculamos el número de quincenas entre dos fechas dadas

´´´Swift
// Fecha inicio
let inicio: Date = Date()

// Fecha fin
let formatter: DateFormatter = DateFormatter()
formatter.dateFormat = "yyyy/MM/dd"
let fin: Date! = formatter.date(from: "2018/01/15")

let noQuincenas: Int = quincenaConclude(date: fin) - quincenaStart(date: inicio)
print(noQuincenas)
´´´

´´´Swift

import UIKit

func quincenaStart(date: Date) -> Int {
    
    var quincena: Int = 0
    
    let year = Calendar.current.component(.year, from: date)
    let month = Calendar.current.component(.month, from: date)
    let day   = Calendar.current.component(.day, from: date)
    
    // Hacia arriba
    
    if day >= 15 && day <= 31 {
        
        // mes * cadaMesTieneDosQuincenas + 1 quincena
        quincena = (month * 2) + 1
    }
    else if day >= 1 && day <= 14 {
        
        quincena = (month * 2)
    }
    
    return year * 12 * 2 + quincena
}

func quincenaConclude(date: Date) -> Int {
    
    var quincena: Int = 0
    
    let year = Calendar.current.component(.year, from: date)
    let month = Calendar.current.component(.month, from: date)
    let day   = Calendar.current.component(.day, from: date)
    
    // Hacia abajo
    
    if day >= 1 && day <= 14 {
        
        quincena = (month * 2) - 1
    }
    else if day >= 15 && day <= 31 {
        
        // mes * cadaMesTieneDosQuincenas + 1 quincena
        quincena = (month * 2)
        
    }
    
    return year * 12 * 2 + quincena
    
}
´´´


