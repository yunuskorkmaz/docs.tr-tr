---
title: 'Nasıl yapılır: Imzasız türleri alan bir Windows Işlevi çağırma (Visual Basic)'
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
ms.openlocfilehash: 97075fb6149ed8c0ce06318d0e5bb6f01b841f30
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053325"
---
# <a name="how-to-call-a-windows-function-that-takes-unsigned-types-visual-basic"></a>Nasıl yapılır: Imzasız türleri alan bir Windows Işlevi çağırma (Visual Basic)

İşaretsiz tamsayı türleri üyelerine sahip bir sınıf, modül veya yapı kullanıyorsanız, bu üyelere Visual Basic erişebilirsiniz.

## <a name="to-call-a-windows-function-that-takes-an-unsigned-type"></a>İşaretsiz bir tür alan bir Windows işlevini çağırmak için

1. İşlevin hangi kitaplıkta bulunduğunu, adının bu kitaplıkta ne olduğunu, ne zaman arama sırasının ne olduğunu ve çağrı sırasında dizelerin nasıl dönüştürüleceğini Visual Basic söylemek için bir [Declare bildirimi](../../../visual-basic/language-reference/statements/declare-statement.md) kullanın.

2. `ULong` `UShort` İfadesinde,`UInteger`,, veya`Byte` imzasız bir tür ile her parametreye uygun şekilde kullanın. `Declare`

3. Kullandığı sabitlerin adlarını ve değerlerini bulmak için, aradığınız Windows işlevinin belgelerini inceleyin. Bunlardan birçoğu WinUser. h dosyasında tanımlanmıştır.

4. Kodunuzda gerekli sabitleri bildirin. Birçok Windows sabiti 32 bitlik işaretsiz değerlerdir ve bunları `As UInteger`bildirmeniz gerekir.

5. İşlevi normal şekilde çağırın. Aşağıdaki örnek, işaretsiz bir tamsayı bağımsız `MessageBox`değişkeni alan Windows işlevini çağırır.

    ```vb
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

     İşlevi `messageThroughWindows` aşağıdaki kodla test edebilirsiniz.

    ```vb
    Public Sub consumeWindowsMessage()
        Dim w As New windowsMessage
        w.messageThroughWindows()
    End Sub
    ```

    > [!CAUTION]
    > `UInteger` ,`ULong`, Ve veri`SByte` türleri [Dil bağımsızlığı ve dilden bağımsız bileşenlerin](../../../standard/language-independence-and-language-independent-components.md) (CLS) bir parçası değildir, bu nedenle CLS uyumlu kod bunları kullanan bir bileşeni tüketemez. `UShort`

    > [!IMPORTANT]
    > Windows uygulama programlama arabirimi (API) gibi yönetilmeyen koda çağrı yapmak, kodunuzu olası güvenlik risklerine sunar.

    > [!IMPORTANT]
    > Windows API 'sinin çağrılması, yönetilmeyen kod iznini gerektirir, bu da kısmi güven durumlarında yürütmesini etkileyebilir. Daha fazla bilgi için bkz <xref:System.Security.Permissions.SecurityPermission> . ve [kod erişim izinleri](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/h846e9b3(v=vs.100)).

## <a name="see-also"></a>Ayrıca bkz.

- [Veri Türleri](../../../visual-basic/language-reference/data-types/index.md)
- [Integer Veri Türü](../../../visual-basic/language-reference/data-types/integer-data-type.md)
- [UInteger Veri Türü](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)
- [Declare Deyimi](../../../visual-basic/language-reference/statements/declare-statement.md)
- [İzlenecek yol: Windows API'lerini Çağırma](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)
