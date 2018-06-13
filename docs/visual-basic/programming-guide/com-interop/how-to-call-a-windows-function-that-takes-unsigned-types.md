---
title: 'Nasıl yapılır: İmzalanmamış Türler İsteyen Bir Windows İşlevi Çağırma (Visual Basic)'
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
ms.openlocfilehash: afec9965c4ff728094e901eb4924ac94c432b300
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33643032"
---
# <a name="how-to-call-a-windows-function-that-takes-unsigned-types-visual-basic"></a><span data-ttu-id="8a558-102">Nasıl yapılır: İmzalanmamış Türler İsteyen Bir Windows İşlevi Çağırma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8a558-102">How to: Call a Windows Function that Takes Unsigned Types (Visual Basic)</span></span>
<span data-ttu-id="8a558-103">Bir sınıf, modül veya imzasız tamsayı türleri üyeleri olan yapısı kullanıyorsa, Visual Basic ile bu üyeleri erişebilir.</span><span class="sxs-lookup"><span data-stu-id="8a558-103">If you are consuming a class, module, or structure that has members of unsigned integer types, you can access these members with Visual Basic.</span></span>  
  
### <a name="to-call-a-windows-function-that-takes-an-unsigned-type"></a><span data-ttu-id="8a558-104">İşaretsiz tür geçen bir Windows işlevi çağırma</span><span class="sxs-lookup"><span data-stu-id="8a558-104">To call a Windows function that takes an unsigned type</span></span>  
  
1.  <span data-ttu-id="8a558-105">Kullanım bir [Declare deyimi](../../../visual-basic/language-reference/statements/declare-statement.md) Visual Basic işlevi hangi kitaplığı tutar, bu kitaplığın adı nedir, kendi arama sırası nedir ve bunu çağrılırken dizeleri dönüştürme bildirmek için.</span><span class="sxs-lookup"><span data-stu-id="8a558-105">Use a [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) to tell Visual Basic which library holds the function, what its name is in that library, what its calling sequence is, and how to convert strings when calling it.</span></span>  
  
2.  <span data-ttu-id="8a558-106">İçinde `Declare` deyimi, kullanım `UInteger`, `ULong`, `UShort`, veya `Byte` imzasız türe sahip her parametre için uygun şekilde.</span><span class="sxs-lookup"><span data-stu-id="8a558-106">In the `Declare` statement, use `UInteger`, `ULong`, `UShort`, or `Byte` as appropriate for each parameter with an unsigned type.</span></span>  
  
3.  <span data-ttu-id="8a558-107">Adları ve değerleri kullanır sabitlerin bulmak için aradığınız Windows işlevi için belgelere bakın.</span><span class="sxs-lookup"><span data-stu-id="8a558-107">Consult the documentation for the Windows function you are calling to find the names and values of the constants it uses.</span></span> <span data-ttu-id="8a558-108">Bunların çoğu WinUser.h dosyasında tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="8a558-108">Many of these are defined in the WinUser.h file.</span></span>  
  
4.  <span data-ttu-id="8a558-109">Kodunuzda gerekli sabitleri bildirin.</span><span class="sxs-lookup"><span data-stu-id="8a558-109">Declare the necessary constants in your code.</span></span> <span data-ttu-id="8a558-110">Çok sayıda Windows sabitler 32-bit işaretsiz değerlerdir ve bunlar bildirmelidir `As``UInteger`.</span><span class="sxs-lookup"><span data-stu-id="8a558-110">Many Windows constants are 32-bit unsigned values, and you should declare these `As``UInteger`.</span></span>  
  
5.  <span data-ttu-id="8a558-111">Normal bir şekilde işlevini çağırın.</span><span class="sxs-lookup"><span data-stu-id="8a558-111">Call the function in the normal way.</span></span> <span data-ttu-id="8a558-112">Aşağıdaki örnek Windows işlevini çağırır `MessageBox`, bir işaretsiz tamsayı bağımsız değişkeni alır.</span><span class="sxs-lookup"><span data-stu-id="8a558-112">The following example calls the Windows function `MessageBox`, which takes an unsigned integer argument.</span></span>  
  
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
  
     <span data-ttu-id="8a558-113">İşlevi test `messageThroughWindows` aşağıdaki kod ile.</span><span class="sxs-lookup"><span data-stu-id="8a558-113">You can test the function `messageThroughWindows` with the following code.</span></span>  
  
    ```  
    Public Sub consumeWindowsMessage()  
        Dim w As New windowsMessage  
        w.messageThroughWindows()  
    End Sub  
    ```  
  
    > [!CAUTION]
    >  <span data-ttu-id="8a558-114">`UInteger`, `ULong`, `UShort`, Ve `SByte` veri türleri olmayan parçası [dil bağımsızlığı ve dilden bağımsız bileşenler](../../../standard/language-independence-and-language-independent-components.md) (CLS), CLS uyumlu kod bir component kullanamayacaklarını şekilde, bunları kullanır.</span><span class="sxs-lookup"><span data-stu-id="8a558-114">The `UInteger`, `ULong`, `UShort`, and `SByte` data types are not part of the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), so CLS-compliant code cannot consume a component that uses them.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="8a558-115">Windows uygulama programlama arabirimi gibi (API), yönetilmeyen kod aradığı kodunuzu olası güvenlik risklerini kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="8a558-115">Making a call to unmanaged code, such as the Windows application programming interface (API), exposes your code to potential security risks.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="8a558-116">Windows API'si çağırma kısmi güven durumlarda yürütülmesinin etkileyebilecek yönetilmeyen kod izni gerektirir.</span><span class="sxs-lookup"><span data-stu-id="8a558-116">Calling the Windows API requires unmanaged code permission, which might affect its execution in partial-trust situations.</span></span> <span data-ttu-id="8a558-117">Daha fazla bilgi için bkz: <xref:System.Security.Permissions.SecurityPermission> ve [kod erişim izinleri](http://msdn.microsoft.com/library/e5ae402f-6dda-4732-bbe8-77296630f675).</span><span class="sxs-lookup"><span data-stu-id="8a558-117">For more information, see <xref:System.Security.Permissions.SecurityPermission> and [Code Access Permissions](http://msdn.microsoft.com/library/e5ae402f-6dda-4732-bbe8-77296630f675).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a558-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8a558-118">See Also</span></span>  
 [<span data-ttu-id="8a558-119">Veri Türleri</span><span class="sxs-lookup"><span data-stu-id="8a558-119">Data Types</span></span>](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="8a558-120">Integer Veri Türü</span><span class="sxs-lookup"><span data-stu-id="8a558-120">Integer Data Type</span></span>](../../../visual-basic/language-reference/data-types/integer-data-type.md)  
 [<span data-ttu-id="8a558-121">UInteger Veri Türü</span><span class="sxs-lookup"><span data-stu-id="8a558-121">UInteger Data Type</span></span>](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
 [<span data-ttu-id="8a558-122">Declare Deyimi</span><span class="sxs-lookup"><span data-stu-id="8a558-122">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
 [<span data-ttu-id="8a558-123">İzlenecek yol: Windows API'lerini Çağırma</span><span class="sxs-lookup"><span data-stu-id="8a558-123">Walkthrough: Calling Windows APIs</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)
