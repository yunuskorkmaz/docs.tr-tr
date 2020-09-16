---
title: 'Nasıl yapılır: İmzalanmamış Türler İsteyen Bir Windows İşlevi Çağırma'
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
ms.openlocfilehash: 5b78c808de4a16060d37844ad0f17e89fa6f6d84
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90548084"
---
# <a name="how-to-call-a-windows-function-that-takes-unsigned-types-visual-basic"></a><span data-ttu-id="b4800-102">Nasıl yapılır: İmzalanmamış Türler İsteyen Bir Windows İşlevi Çağırma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b4800-102">How to: Call a Windows Function that Takes Unsigned Types (Visual Basic)</span></span>

<span data-ttu-id="b4800-103">İşaretsiz tamsayı türleri üyelerine sahip bir sınıf, modül veya yapı kullanıyorsanız, bu üyelere Visual Basic erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b4800-103">If you are consuming a class, module, or structure that has members of unsigned integer types, you can access these members with Visual Basic.</span></span>

## <a name="to-call-a-windows-function-that-takes-an-unsigned-type"></a><span data-ttu-id="b4800-104">İşaretsiz bir tür alan bir Windows işlevini çağırmak için</span><span class="sxs-lookup"><span data-stu-id="b4800-104">To call a Windows function that takes an unsigned type</span></span>

1. <span data-ttu-id="b4800-105">İşlevin hangi kitaplıkta bulunduğunu, adının bu kitaplıkta ne olduğunu, ne zaman arama sırasının ne olduğunu ve çağrı sırasında dizelerin nasıl dönüştürüleceğini Visual Basic söylemek için bir [Declare bildirimi](../../language-reference/statements/declare-statement.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="b4800-105">Use a [Declare Statement](../../language-reference/statements/declare-statement.md) to tell Visual Basic which library holds the function, what its name is in that library, what its calling sequence is, and how to convert strings when calling it.</span></span>

2. <span data-ttu-id="b4800-106">İfadesinde,,, `Declare` `UInteger` `ULong` `UShort` veya `Byte` imzasız bir tür ile her parametreye uygun şekilde kullanın.</span><span class="sxs-lookup"><span data-stu-id="b4800-106">In the `Declare` statement, use `UInteger`, `ULong`, `UShort`, or `Byte` as appropriate for each parameter with an unsigned type.</span></span>

3. <span data-ttu-id="b4800-107">Kullandığı sabitlerin adlarını ve değerlerini bulmak için, aradığınız Windows işlevinin belgelerini inceleyin.</span><span class="sxs-lookup"><span data-stu-id="b4800-107">Consult the documentation for the Windows function you are calling to find the names and values of the constants it uses.</span></span> <span data-ttu-id="b4800-108">Bunlardan birçoğu WinUser. h dosyasında tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="b4800-108">Many of these are defined in the WinUser.h file.</span></span>

4. <span data-ttu-id="b4800-109">Kodunuzda gerekli sabitleri bildirin.</span><span class="sxs-lookup"><span data-stu-id="b4800-109">Declare the necessary constants in your code.</span></span> <span data-ttu-id="b4800-110">Birçok Windows sabiti 32 bitlik işaretsiz değerlerdir ve bunları bildirmeniz gerekir `As UInteger` .</span><span class="sxs-lookup"><span data-stu-id="b4800-110">Many Windows constants are 32-bit unsigned values, and you should declare these `As UInteger`.</span></span>

5. <span data-ttu-id="b4800-111">İşlevi normal şekilde çağırın.</span><span class="sxs-lookup"><span data-stu-id="b4800-111">Call the function in the normal way.</span></span> <span data-ttu-id="b4800-112">Aşağıdaki örnek, `MessageBox` işaretsiz bir tamsayı bağımsız değişkeni alan Windows işlevini çağırır.</span><span class="sxs-lookup"><span data-stu-id="b4800-112">The following example calls the Windows function `MessageBox`, which takes an unsigned integer argument.</span></span>

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

     <span data-ttu-id="b4800-113">İşlevi aşağıdaki kodla test edebilirsiniz `messageThroughWindows` .</span><span class="sxs-lookup"><span data-stu-id="b4800-113">You can test the function `messageThroughWindows` with the following code.</span></span>

    ```vb
    Public Sub consumeWindowsMessage()
        Dim w As New windowsMessage
        w.messageThroughWindows()
    End Sub
    ```

    > [!CAUTION]
    > <span data-ttu-id="b4800-114">`UInteger`,, `ULong` `UShort` Ve `SByte` veri türleri [Dil bağımsızlığı ve dilden bağımsız bileşenlerin](../../../standard/language-independence-and-language-independent-components.md) (CLS) bir parçası değildir, bu nedenle CLS uyumlu kod bunları kullanan bir bileşeni tüketemez.</span><span class="sxs-lookup"><span data-stu-id="b4800-114">The `UInteger`, `ULong`, `UShort`, and `SByte` data types are not part of the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), so CLS-compliant code cannot consume a component that uses them.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="b4800-115">Windows uygulama programlama arabirimi (API) gibi yönetilmeyen koda çağrı yapmak, kodunuzu olası güvenlik risklerine sunar.</span><span class="sxs-lookup"><span data-stu-id="b4800-115">Making a call to unmanaged code, such as the Windows application programming interface (API), exposes your code to potential security risks.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="b4800-116">Windows API 'sinin çağrılması, yönetilmeyen kod iznini gerektirir, bu da kısmi güven durumlarında yürütmesini etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="b4800-116">Calling the Windows API requires unmanaged code permission, which might affect its execution in partial-trust situations.</span></span> <span data-ttu-id="b4800-117">Daha fazla bilgi için bkz <xref:System.Security.Permissions.SecurityPermission> . ve [kod erişim izinleri](/previous-versions/dotnet/netframework-4.0/h846e9b3(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="b4800-117">For more information, see <xref:System.Security.Permissions.SecurityPermission> and [Code Access Permissions](/previous-versions/dotnet/netframework-4.0/h846e9b3(v=vs.100)).</span></span>

## <a name="see-also"></a><span data-ttu-id="b4800-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b4800-118">See also</span></span>

- [<span data-ttu-id="b4800-119">Veri türleri</span><span class="sxs-lookup"><span data-stu-id="b4800-119">Data Types</span></span>](../../language-reference/data-types/index.md)
- [<span data-ttu-id="b4800-120">Integer Veri Türü</span><span class="sxs-lookup"><span data-stu-id="b4800-120">Integer Data Type</span></span>](../../language-reference/data-types/integer-data-type.md)
- [<span data-ttu-id="b4800-121">UInteger Veri Türü</span><span class="sxs-lookup"><span data-stu-id="b4800-121">UInteger Data Type</span></span>](../../language-reference/data-types/uinteger-data-type.md)
- [<span data-ttu-id="b4800-122">Declare Deyimi</span><span class="sxs-lookup"><span data-stu-id="b4800-122">Declare Statement</span></span>](../../language-reference/statements/declare-statement.md)
- [<span data-ttu-id="b4800-123">İzlenecek yol: Windows API'lerini Çağırma</span><span class="sxs-lookup"><span data-stu-id="b4800-123">Walkthrough: Calling Windows APIs</span></span>](walkthrough-calling-windows-apis.md)
