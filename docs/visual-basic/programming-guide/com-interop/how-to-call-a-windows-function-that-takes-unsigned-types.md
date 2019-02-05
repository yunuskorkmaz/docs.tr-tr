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
ms.openlocfilehash: e31bc2f9a0b20ce168004fa3ea2210d39a23761e
ms.sourcegitcommit: facefcacd7ae2e5645e463bc841df213c505ffd4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/05/2019
ms.locfileid: "55738623"
---
# <a name="how-to-call-a-windows-function-that-takes-unsigned-types-visual-basic"></a><span data-ttu-id="8b3dd-102">Nasıl yapılır: (Visual Basic) imzalanmamış türler isteyen bir Windows işlevi çağırma</span><span class="sxs-lookup"><span data-stu-id="8b3dd-102">How to: Call a Windows Function that Takes Unsigned Types (Visual Basic)</span></span>
<span data-ttu-id="8b3dd-103">Bir sınıf, modül veya işaretsiz tamsayı türlerinin üyelerini içeren yapı kullanıyorsa, Visual Basic ile bu üyeleri erişebilir.</span><span class="sxs-lookup"><span data-stu-id="8b3dd-103">If you are consuming a class, module, or structure that has members of unsigned integer types, you can access these members with Visual Basic.</span></span>  
  
### <a name="to-call-a-windows-function-that-takes-an-unsigned-type"></a><span data-ttu-id="8b3dd-104">Bir işaretsiz türe almayan bir Windows işlevi çağırma</span><span class="sxs-lookup"><span data-stu-id="8b3dd-104">To call a Windows function that takes an unsigned type</span></span>  
  
1.  <span data-ttu-id="8b3dd-105">Kullanım bir [Declare Deyimi'nin](../../../visual-basic/language-reference/statements/declare-statement.md) hangi kitaplığı işlevi tutar, bu kitaplıkta adı nedir, kendi çağrı sırası nedir ve nasıl çağırırken dizeleri dönüştürmek Visual Basic söylemek için.</span><span class="sxs-lookup"><span data-stu-id="8b3dd-105">Use a [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) to tell Visual Basic which library holds the function, what its name is in that library, what its calling sequence is, and how to convert strings when calling it.</span></span>  
  
2.  <span data-ttu-id="8b3dd-106">İçinde `Declare` deyimi, kullanım `UInteger`, `ULong`, `UShort`, veya `Byte` uygun şekilde her bir parametreye bir işaretsiz türe sahip.</span><span class="sxs-lookup"><span data-stu-id="8b3dd-106">In the `Declare` statement, use `UInteger`, `ULong`, `UShort`, or `Byte` as appropriate for each parameter with an unsigned type.</span></span>  
  
3.  <span data-ttu-id="8b3dd-107">Windows işlev adlarını ve değerlerini kullanır sabitlerin bulmak için arama için belgelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="8b3dd-107">Consult the documentation for the Windows function you are calling to find the names and values of the constants it uses.</span></span> <span data-ttu-id="8b3dd-108">Bunların çoğu WinUser.h dosyasında tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="8b3dd-108">Many of these are defined in the WinUser.h file.</span></span>  
  
4.  <span data-ttu-id="8b3dd-109">Kodunuzu gerekli sabitlerle bildirin.</span><span class="sxs-lookup"><span data-stu-id="8b3dd-109">Declare the necessary constants in your code.</span></span> <span data-ttu-id="8b3dd-110">32-bit işeritsiz değerler birçok Windows sabittir ve bunlar bildirmelidir `As UInteger`.</span><span class="sxs-lookup"><span data-stu-id="8b3dd-110">Many Windows constants are 32-bit unsigned values, and you should declare these `As UInteger`.</span></span>  
  
5.  <span data-ttu-id="8b3dd-111">İşlevi, normal bir şekilde çağırın.</span><span class="sxs-lookup"><span data-stu-id="8b3dd-111">Call the function in the normal way.</span></span> <span data-ttu-id="8b3dd-112">Aşağıdaki örnek Windows işlevini çağırır `MessageBox`, işaretsiz tamsayı bağımsız değişken alır.</span><span class="sxs-lookup"><span data-stu-id="8b3dd-112">The following example calls the Windows function `MessageBox`, which takes an unsigned integer argument.</span></span>  
  
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
  
     <span data-ttu-id="8b3dd-113">İşlevi test edebilirsiniz `messageThroughWindows` aşağıdaki kod ile.</span><span class="sxs-lookup"><span data-stu-id="8b3dd-113">You can test the function `messageThroughWindows` with the following code.</span></span>  
  
    ```  
    Public Sub consumeWindowsMessage()  
        Dim w As New windowsMessage  
        w.messageThroughWindows()  
    End Sub  
    ```  
  
    > [!CAUTION]
    >  <span data-ttu-id="8b3dd-114">`UInteger`, `ULong`, `UShort`, Ve `SByte` veri türleri parçası [dil bağımsızlığı ve dilden bağımsız bileşenler](../../../standard/language-independence-and-language-independent-components.md) (CLS), CLS uyumlu kod bir bileşen kullanamıyor. Bu nedenle, bunları kullanır.</span><span class="sxs-lookup"><span data-stu-id="8b3dd-114">The `UInteger`, `ULong`, `UShort`, and `SByte` data types are not part of the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), so CLS-compliant code cannot consume a component that uses them.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="8b3dd-115">Windows uygulama programlama arabirimi gibi (API), yönetilmeyen kod çağırmak, olası güvenlik risklerini kodunuza kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="8b3dd-115">Making a call to unmanaged code, such as the Windows application programming interface (API), exposes your code to potential security risks.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="8b3dd-116">Windows API çağırmak, kısmi güven durumlarında yürütme şeklinizi etkileyebilecek olan yönetilmeyen kod iznini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="8b3dd-116">Calling the Windows API requires unmanaged code permission, which might affect its execution in partial-trust situations.</span></span> <span data-ttu-id="8b3dd-117">Daha fazla bilgi için <xref:System.Security.Permissions.SecurityPermission> ve [kod erişim izinleri](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/h846e9b3(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="8b3dd-117">For more information, see <xref:System.Security.Permissions.SecurityPermission> and [Code Access Permissions](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/h846e9b3(v=vs.100)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b3dd-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8b3dd-118">See also</span></span>
- [<span data-ttu-id="8b3dd-119">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="8b3dd-119">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="8b3dd-120">Integer Veri Türü</span><span class="sxs-lookup"><span data-stu-id="8b3dd-120">Integer Data Type</span></span>](../../../visual-basic/language-reference/data-types/integer-data-type.md)
- [<span data-ttu-id="8b3dd-121">UInteger Veri Türü</span><span class="sxs-lookup"><span data-stu-id="8b3dd-121">UInteger Data Type</span></span>](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)
- [<span data-ttu-id="8b3dd-122">Declare Deyimi</span><span class="sxs-lookup"><span data-stu-id="8b3dd-122">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)
- [<span data-ttu-id="8b3dd-123">İzlenecek yol: Windows API'lerini Çağırma</span><span class="sxs-lookup"><span data-stu-id="8b3dd-123">Walkthrough: Calling Windows APIs</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)
