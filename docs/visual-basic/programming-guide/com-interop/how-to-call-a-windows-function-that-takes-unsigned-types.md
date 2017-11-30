---
title: "Nasıl yapılır: İmzalanmamış Türler İsteyen Bir Windows İşlevi Çağırma (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Windows functions [Visual Basic], calling
- unsigned data types [Visual Basic]
- UShort data type [Visual Basic], using
- functions [Visual Basic], calling Windows functions
- ULong data type [Visual Basic], using
- UInteger data type [Visual Basic], using
- data types [Visual Basic], using
- unsigned types [Visual Basic]
- data types [Visual Basic], unsigned
- data types [Visual Basic], numeric
- unsigned types [Visual Basic], using
ms.assetid: c2c0e712-8dc2-43b9-b4c6-345fbb02e7ce
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d1d59c29a83ede97d90926c8e499788676e2c235
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-call-a-windows-function-that-takes-unsigned-types-visual-basic"></a>Nasıl yapılır: İmzalanmamış Türler İsteyen Bir Windows İşlevi Çağırma (Visual Basic)
Bir sınıf, modül veya imzasız tamsayı türleri üyeleri olan yapısı kullanıyorsa, bu üyelerle erişebilirsiniz [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].  
  
### <a name="to-call-a-windows-function-that-takes-an-unsigned-type"></a>İşaretsiz tür geçen bir Windows işlevi çağırma  
  
1.  Kullanım bir [Declare deyimi](../../../visual-basic/language-reference/statements/declare-statement.md) bildirmek için [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] işlevi hangi kitaplığı tutar, bu kitaplığın adı nedir, kendi arama sırası nedir ve bunu çağrılırken dizeleri dönüştürme.  
  
2.  İçinde `Declare` deyimi, kullanım `UInteger`, `ULong`, `UShort`, veya `Byte` imzasız türe sahip her parametre için uygun şekilde.  
  
3.  Adları ve değerleri kullanır sabitlerin bulmak için aradığınız Windows işlevi için belgelere bakın. Bunların çoğu WinUser.h dosyasında tanımlanır.  
  
4.  Kodunuzda gerekli sabitleri bildirin. Çok sayıda Windows sabitler 32-bit işaretsiz değerlerdir ve bunlar bildirmelidir `As``UInteger`.  
  
5.  Normal bir şekilde işlevini çağırın. Aşağıdaki örnek Windows işlevini çağırır `MessageBox`, bir işaretsiz tamsayı bağımsız değişkeni alır.  
  
    ```  
    Public Class windowsMessage  
        Private Declare Auto Function mb Lib "user32.dll" Alias "MessageBox" (  
            ByVal hWnd As Integer,   
            ByVal lpText As String,   
            ByVal lpCaption As String,   
            ByVal uType As UInteger) As Integer  
        Private Const MB_OK As UInteger = 0  
        Private Const MB_ICONEXCLAMATION As UInteger = &H30  
        Private Const IDOK As UInteger = 1  
        Private Const IDCLOSE As UInteger = 8  
        Private Const c As UInteger = MB_OK Or MB_ICONEXCLAMATION  
        Public Function messageThroughWindows() As String  
            Dim r As Integer = mb(0, "Click OK if you see this!",   
                "Windows API call", c)  
            Dim s As String = "Windows API MessageBox returned " &  
                 CStr(r)& vbCrLf & "(IDOK = " & CStr(IDOK) &  
                 ", IDCLOSE = " & CStr(IDCLOSE) & ")"  
            Return s  
        End Function  
    End Class  
    ```  
  
     İşlevi test `messageThroughWindows` aşağıdaki kod ile.  
  
    ```  
    Public Sub consumeWindowsMessage()  
        Dim w As New windowsMessage  
        w.messageThroughWindows()  
    End Sub  
    ```  
  
    > [!CAUTION]
    >  `UInteger`, `ULong`, `UShort`, Ve `SByte` veri türleri olmayan parçası [dil bağımsızlığı ve dilden bağımsız bileşenler](https://msdn.microsoft.com/library/12a7a7h3) (CLS), CLS uyumlu kod bir component kullanamayacaklarını şekilde, bunları kullanır.  
  
    > [!IMPORTANT]
    >  Windows uygulama programlama arabirimi gibi (API), yönetilmeyen kod aradığı kodunuzu olası güvenlik risklerini kullanıma sunar.  
  
    > [!IMPORTANT]
    >  Windows API'si çağırma kısmi güven durumlarda yürütülmesinin etkileyebilecek yönetilmeyen kod izni gerektirir. Daha fazla bilgi için bkz: <xref:System.Security.Permissions.SecurityPermission> ve [kod erişim izinleri](http://msdn.microsoft.com/en-us/e5ae402f-6dda-4732-bbe8-77296630f675).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri türleri](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [Integer veri türü](../../../visual-basic/language-reference/data-types/integer-data-type.md)  
 [Uınteger veri türü](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
 [Declare deyimi](../../../visual-basic/language-reference/statements/declare-statement.md)  
 [İzlenecek yol: Windows API'larını çağırma](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)
