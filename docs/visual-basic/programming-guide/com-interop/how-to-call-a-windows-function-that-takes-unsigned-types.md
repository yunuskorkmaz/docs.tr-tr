---
title: 'Nasıl yapılır: (Visual Basic) imzalanmamış türler isteyen bir Windows işlevi çağırma'
ms.date: 07/20/2015
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
ms.openlocfilehash: 092f1acf6e6a8468890a371836979db4e0692d1e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54669321"
---
# <a name="how-to-call-a-windows-function-that-takes-unsigned-types-visual-basic"></a>Nasıl yapılır: (Visual Basic) imzalanmamış türler isteyen bir Windows işlevi çağırma
Bir sınıf, modül veya işaretsiz tamsayı türlerinin üyelerini içeren yapı kullanıyorsa, Visual Basic ile bu üyeleri erişebilir.  
  
### <a name="to-call-a-windows-function-that-takes-an-unsigned-type"></a>Bir işaretsiz türe almayan bir Windows işlevi çağırma  
  
1.  Kullanım bir [Declare Deyimi'nin](../../../visual-basic/language-reference/statements/declare-statement.md) hangi kitaplığı işlevi tutar, bu kitaplıkta adı nedir, kendi çağrı sırası nedir ve nasıl çağırırken dizeleri dönüştürmek Visual Basic söylemek için.  
  
2.  İçinde `Declare` deyimi, kullanım `UInteger`, `ULong`, `UShort`, veya `Byte` uygun şekilde her bir parametreye bir işaretsiz türe sahip.  
  
3.  Windows işlev adlarını ve değerlerini kullanır sabitlerin bulmak için arama için belgelerine bakın. Bunların çoğu WinUser.h dosyasında tanımlanır.  
  
4.  Kodunuzu gerekli sabitlerle bildirin. 32-bit işeritsiz değerler birçok Windows sabittir ve bunlar bildirmelidir `As``UInteger`.  
  
5.  İşlevi, normal bir şekilde çağırın. Aşağıdaki örnek Windows işlevini çağırır `MessageBox`, işaretsiz tamsayı bağımsız değişken alır.  
  
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
  
     İşlevi test edebilirsiniz `messageThroughWindows` aşağıdaki kod ile.  
  
    ```  
    Public Sub consumeWindowsMessage()  
        Dim w As New windowsMessage  
        w.messageThroughWindows()  
    End Sub  
    ```  
  
    > [!CAUTION]
    >  `UInteger`, `ULong`, `UShort`, Ve `SByte` veri türleri parçası [dil bağımsızlığı ve dilden bağımsız bileşenler](../../../standard/language-independence-and-language-independent-components.md) (CLS), CLS uyumlu kod bir bileşen kullanamıyor. Bu nedenle, bunları kullanır.  
  
    > [!IMPORTANT]
    >  Windows uygulama programlama arabirimi gibi (API), yönetilmeyen kod çağırmak, olası güvenlik risklerini kodunuza kullanıma sunar.  
  
    > [!IMPORTANT]
    >  Windows API çağırmak, kısmi güven durumlarında yürütme şeklinizi etkileyebilecek olan yönetilmeyen kod iznini gerektirir. Daha fazla bilgi için <xref:System.Security.Permissions.SecurityPermission> ve [kod erişim izinleri](https://msdn.microsoft.com/library/e5ae402f-6dda-4732-bbe8-77296630f675).  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Veri Türleri](../../../visual-basic/language-reference/data-types/index.md)
- [Integer Veri Türü](../../../visual-basic/language-reference/data-types/integer-data-type.md)
- [UInteger Veri Türü](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)
- [Declare Deyimi](../../../visual-basic/language-reference/statements/declare-statement.md)
- [İzlenecek yol: Windows API'lerini Çağırma](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)
