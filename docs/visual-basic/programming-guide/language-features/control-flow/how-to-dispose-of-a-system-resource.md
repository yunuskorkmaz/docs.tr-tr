---
title: 'Nasıl yapılır: Bir Sistem Kaynağını Atma'
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
ms.openlocfilehash: c493051050442597196ba484fb9ce8e99249dbb7
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353938"
---
# <a name="how-to-dispose-of-a-system-resource-visual-basic"></a><span data-ttu-id="d982f-102">Nasıl yapılır: Bir Sistem Kaynağını Atma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d982f-102">How to: Dispose of a System Resource (Visual Basic)</span></span>
<span data-ttu-id="d982f-103">Kodunuzun bloğundan çıkılırken sistemin bir kaynağı ortadan kaldırabileceğini garantilemek için `Using` bloğu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d982f-103">You can use a `Using` block to guarantee that the system disposes of a resource when your code exits the block.</span></span> <span data-ttu-id="d982f-104">Bu, büyük miktarda bellek tüketen bir sistem kaynağı kullanıyorsanız veya diğer bileşenlerin de kullanılmasını istiyorsanız kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="d982f-104">This is useful if you are using a system resource that consumes a large amount of memory, or that other components also want to use.</span></span>  
  
### <a name="to-dispose-of-a-database-connection-when-your-code-is-finished-with-it"></a><span data-ttu-id="d982f-105">Kodunuz ile işiniz bittiğinde bir veritabanı bağlantısını atmak için</span><span class="sxs-lookup"><span data-stu-id="d982f-105">To dispose of a database connection when your code is finished with it</span></span>  
  
1. <span data-ttu-id="d982f-106">Kaynak dosyanızın başlangıcında (Bu durumda, <xref:System.Data.SqlClient>) veritabanı bağlantısı için uygun [Imports bildirisini (.net ad alanı ve türü)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) eklediğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="d982f-106">Make sure you include the appropriate [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) for the database connection at the beginning of your source file (in this case, <xref:System.Data.SqlClient>).</span></span>  
  
2. <span data-ttu-id="d982f-107">`Using` ve `End Using` deyimleriyle `Using` bloğu oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d982f-107">Create a `Using` block with the `Using` and `End Using` statements.</span></span> <span data-ttu-id="d982f-108">Bloğun içinde, veritabanı bağlantısıyla ilgilenen kodu koyun.</span><span class="sxs-lookup"><span data-stu-id="d982f-108">Inside the block, put the code that deals with the database connection.</span></span>  
  
3. <span data-ttu-id="d982f-109">Bağlantıyı bildirin ve `Using` deyimin bir parçası olarak bir örneğini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d982f-109">Declare the connection and create an instance of it as part of the `Using` statement.</span></span>  
  
    ```vb  
    ' Insert the following line at the beginning of your source file.  
    Imports System.Data.SqlClient  
    Public Sub AccessSql(ByVal s As String)  
        Using sqc As New System.Data.SqlClient.SqlConnection(s)  
            MsgBox("Connected with string """ & sqc.ConnectionString & """")  
        End Using  
    End Sub  
    ```  
  
     <span data-ttu-id="d982f-110">İşlenmeyen bir özel durum da dahil olmak üzere bloğundan çıktığınızda sistem kaynağı ortadan kaldırsın.</span><span class="sxs-lookup"><span data-stu-id="d982f-110">The system disposes of the resource no matter how you exit the block, including the case of an unhandled exception.</span></span>  
  
     <span data-ttu-id="d982f-111">Kapsamı bloğa sınırlı olduğundan, `Using` bloğunun dışından `sqc` erişemediğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="d982f-111">Note that you cannot access `sqc` from outside the `Using` block, because its scope is limited to the block.</span></span>  
  
     <span data-ttu-id="d982f-112">Bu tekniği, bir dosya tanıtıcısı veya bir COM sarmalayıcı gibi bir sistem kaynağı üzerinde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d982f-112">You can use this same technique on a system resource such as a file handle or a COM wrapper.</span></span> <span data-ttu-id="d982f-113">`Using` bloğundan çıktıktan sonra kaynağın diğer bileşenler için kullanılabilir durumda kalmasını sağlamak istediğinizde bir `Using` bloğu kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="d982f-113">You use a `Using` block when you want to be sure to leave the resource available for other components after you have exited the `Using` block.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d982f-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d982f-114">See also</span></span>

- <xref:System.Data.SqlClient.SqlConnection>
- [<span data-ttu-id="d982f-115">Denetim Akışı</span><span class="sxs-lookup"><span data-stu-id="d982f-115">Control Flow</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [<span data-ttu-id="d982f-116">Karar Yapıları</span><span class="sxs-lookup"><span data-stu-id="d982f-116">Decision Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)
- [<span data-ttu-id="d982f-117">Döngü Yapıları</span><span class="sxs-lookup"><span data-stu-id="d982f-117">Loop Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [<span data-ttu-id="d982f-118">Diğer Denetim Yapıları</span><span class="sxs-lookup"><span data-stu-id="d982f-118">Other Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)
- [<span data-ttu-id="d982f-119">İç İçe Geçmiş Denetim Yapıları</span><span class="sxs-lookup"><span data-stu-id="d982f-119">Nested Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [<span data-ttu-id="d982f-120">Using Deyimi</span><span class="sxs-lookup"><span data-stu-id="d982f-120">Using Statement</span></span>](../../../../visual-basic/language-reference/statements/using-statement.md)
