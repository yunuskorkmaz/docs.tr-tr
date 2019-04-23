---
title: 'Nasıl yapılır: (Visual Basic) bir sistem kaynağını atma'
ms.date: 07/20/2015
helpviewer_keywords:
- Using statement [Visual Basic], disposing of system resources
- Visual Basic code, control flow
- system resources, disposing of
- resources [Visual Basic], disposing of system
- system resources
- Using statement [Visual Basic], Using...End Using
- Using block
ms.assetid: 8be2b239-8090-419b-8e7e-bcaa75b0ecc8
ms.openlocfilehash: e3594db036edc3a6288b0373737c1ee26a691a57
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59341913"
---
# <a name="how-to-dispose-of-a-system-resource-visual-basic"></a><span data-ttu-id="fb9bc-102">Nasıl yapılır: (Visual Basic) bir sistem kaynağını atma</span><span class="sxs-lookup"><span data-stu-id="fb9bc-102">How to: Dispose of a System Resource (Visual Basic)</span></span>
<span data-ttu-id="fb9bc-103">Kullanabileceğiniz bir `Using` kodunuzun blok çıktığında sistemin bir kaynağın siler güvence altına almak için blok.</span><span class="sxs-lookup"><span data-stu-id="fb9bc-103">You can use a `Using` block to guarantee that the system disposes of a resource when your code exits the block.</span></span> <span data-ttu-id="fb9bc-104">Bu, büyük miktarda bellek tüketen veya diğer bileşenleri de kullanmak istediğiniz bir sistem kaynağını kullanıyorsanız yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="fb9bc-104">This is useful if you are using a system resource that consumes a large amount of memory, or that other components also want to use.</span></span>  
  
### <a name="to-dispose-of-a-database-connection-when-your-code-is-finished-with-it"></a><span data-ttu-id="fb9bc-105">Bir veritabanı bağlantı ile kodunuzu sona erdiğinde silmek için</span><span class="sxs-lookup"><span data-stu-id="fb9bc-105">To dispose of a database connection when your code is finished with it</span></span>  
  
1. <span data-ttu-id="fb9bc-106">Uygun eklediğinizden emin olun [Imports deyimi (.NET Namespace ve türü)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) kaynak dosyasının başında veritabanı bağlantısı için (Bu durumda, <xref:System.Data.SqlClient>).</span><span class="sxs-lookup"><span data-stu-id="fb9bc-106">Make sure you include the appropriate [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) for the database connection at the beginning of your source file (in this case, <xref:System.Data.SqlClient>).</span></span>  
  
2. <span data-ttu-id="fb9bc-107">Oluşturma bir `Using` ile block `Using` ve `End Using` deyimleri.</span><span class="sxs-lookup"><span data-stu-id="fb9bc-107">Create a `Using` block with the `Using` and `End Using` statements.</span></span> <span data-ttu-id="fb9bc-108">Veritabanı bağlantısı ile ilgilenen bir kod bloğunun içine yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="fb9bc-108">Inside the block, put the code that deals with the database connection.</span></span>  
  
3. <span data-ttu-id="fb9bc-109">Bağlantı bildirme ve bir örneğini bir parçası olarak oluşturma `Using` deyimi.</span><span class="sxs-lookup"><span data-stu-id="fb9bc-109">Declare the connection and create an instance of it as part of the `Using` statement.</span></span>  
  
    ```  
    ' Insert the following line at the beginning of your source file.  
    Imports System.Data.SqlClient  
    Public Sub AccessSql(ByVal s As String)  
        Using sqc As New System.Data.SqlClient.SqlConnection(s)  
            MsgBox("Connected with string """ & sqc.ConnectionString & """")  
        End Using  
    End Sub  
    ```  
  
     <span data-ttu-id="fb9bc-110">İşlenmeyen bir özel durumu içeren blok çıkış ne olursa olsun kaynak sistem siler.</span><span class="sxs-lookup"><span data-stu-id="fb9bc-110">The system disposes of the resource no matter how you exit the block, including the case of an unhandled exception.</span></span>  
  
     <span data-ttu-id="fb9bc-111">Erişemiyorsanız Not `sqc` gelen dışında `Using` kapsamı blokla sınırlı olduğu için engelleyin.</span><span class="sxs-lookup"><span data-stu-id="fb9bc-111">Note that you cannot access `sqc` from outside the `Using` block, because its scope is limited to the block.</span></span>  
  
     <span data-ttu-id="fb9bc-112">Bir dosya tanıtıcısı veya COM sarmalayıcı gibi bir sistem kaynağına aynı tekniği kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fb9bc-112">You can use this same technique on a system resource such as a file handle or a COM wrapper.</span></span> <span data-ttu-id="fb9bc-113">Kullandığınız bir `Using` block emin olmak için çıkılana sonra diğer bileşenleri için kullanılabilen kaynak bırakmak istediğinizde `Using` blok.</span><span class="sxs-lookup"><span data-stu-id="fb9bc-113">You use a `Using` block when you want to be sure to leave the resource available for other components after you have exited the `Using` block.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb9bc-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fb9bc-114">See also</span></span>

- <xref:System.Data.SqlClient.SqlConnection>
- [<span data-ttu-id="fb9bc-115">Denetim Akışı</span><span class="sxs-lookup"><span data-stu-id="fb9bc-115">Control Flow</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [<span data-ttu-id="fb9bc-116">Karar Yapıları</span><span class="sxs-lookup"><span data-stu-id="fb9bc-116">Decision Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)
- [<span data-ttu-id="fb9bc-117">Döngü Yapıları</span><span class="sxs-lookup"><span data-stu-id="fb9bc-117">Loop Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [<span data-ttu-id="fb9bc-118">Diğer Denetim Yapıları</span><span class="sxs-lookup"><span data-stu-id="fb9bc-118">Other Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)
- [<span data-ttu-id="fb9bc-119">İç İçe Geçmiş Denetim Yapıları</span><span class="sxs-lookup"><span data-stu-id="fb9bc-119">Nested Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [<span data-ttu-id="fb9bc-120">Using Deyimi</span><span class="sxs-lookup"><span data-stu-id="fb9bc-120">Using Statement</span></span>](../../../../visual-basic/language-reference/statements/using-statement.md)
