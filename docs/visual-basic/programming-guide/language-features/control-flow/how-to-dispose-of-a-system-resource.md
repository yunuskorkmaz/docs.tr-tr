---
title: "Nasıl yapılır: Bir Sistem Kaynağını Atma (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Using statement [Visual Basic], disposing of system resources
- Visual Basic code, control flow
- system resources, disposing of
- resources [Visual Basic], disposing of system
- system resources
- Using statement [Visual Basic], Using...End Using
- Using block
ms.assetid: 8be2b239-8090-419b-8e7e-bcaa75b0ecc8
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5b5c65c9d123c6f481852eb249cb4d479a180c5b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-dispose-of-a-system-resource-visual-basic"></a><span data-ttu-id="ea8cd-102">Nasıl yapılır: Bir Sistem Kaynağını Atma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ea8cd-102">How to: Dispose of a System Resource (Visual Basic)</span></span>
<span data-ttu-id="ea8cd-103">Kullanabileceğiniz bir `Using` kodunuzu blok çıktığında sistemin bir kaynağın siler güvence altına almak için blok.</span><span class="sxs-lookup"><span data-stu-id="ea8cd-103">You can use a `Using` block to guarantee that the system disposes of a resource when your code exits the block.</span></span> <span data-ttu-id="ea8cd-104">Bu, büyük miktarda bellek tüketir veya diğer bileşenleri de kullanmak istediğiniz bir sistem kaynağı kullanıyorsanız yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="ea8cd-104">This is useful if you are using a system resource that consumes a large amount of memory, or that other components also want to use.</span></span>  
  
### <a name="to-dispose-of-a-database-connection-when-your-code-is-finished-with-it"></a><span data-ttu-id="ea8cd-105">Kodunuz ile sona erdiğinde veritabanı bağlantısını silmek için</span><span class="sxs-lookup"><span data-stu-id="ea8cd-105">To dispose of a database connection when your code is finished with it</span></span>  
  
1.  <span data-ttu-id="ea8cd-106">Uygun eklediğinizden emin olun [Imports deyimi (.NET Namespace ve türü)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) başında veritabanı bağlantısının kaynak dosyasının (Bu durumda, <xref:System.Data.SqlClient>).</span><span class="sxs-lookup"><span data-stu-id="ea8cd-106">Make sure you include the appropriate [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) for the database connection at the beginning of your source file (in this case, <xref:System.Data.SqlClient>).</span></span>  
  
2.  <span data-ttu-id="ea8cd-107">Oluşturma bir `Using` ile engelleme `Using` ve `End Using` deyimleri.</span><span class="sxs-lookup"><span data-stu-id="ea8cd-107">Create a `Using` block with the `Using` and `End Using` statements.</span></span> <span data-ttu-id="ea8cd-108">Veritabanı bağlantısı ile ilgilenir kod bloğunun içine yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="ea8cd-108">Inside the block, put the code that deals with the database connection.</span></span>  
  
3.  <span data-ttu-id="ea8cd-109">Bağlantı bildirme ve bir örneğini bir parçası olarak oluşturma `Using` deyimi.</span><span class="sxs-lookup"><span data-stu-id="ea8cd-109">Declare the connection and create an instance of it as part of the `Using` statement.</span></span>  
  
    ```  
    ' Insert the following line at the beginning of your source file.  
    Imports System.Data.SqlClient  
    Public Sub AccessSql(ByVal s As String)  
        Using sqc As New System.Data.SqlClient.SqlConnection(s)  
            MsgBox("Connected with string """ & sqc.ConnectionString & """")  
        End Using  
    End Sub  
    ```  
  
     <span data-ttu-id="ea8cd-110">İşlenmeyen bir özel durum da dahil olmak üzere, blok çıkmak ne olursa olsun kaynağın sistem siler.</span><span class="sxs-lookup"><span data-stu-id="ea8cd-110">The system disposes of the resource no matter how you exit the block, including the case of an unhandled exception.</span></span>  
  
     <span data-ttu-id="ea8cd-111">Erişemediğiniz Not `sqc` gelen dışında `Using` kapsamı bloğu ile sınırlı olduğundan engelleyin.</span><span class="sxs-lookup"><span data-stu-id="ea8cd-111">Note that you cannot access `sqc` from outside the `Using` block, because its scope is limited to the block.</span></span>  
  
     <span data-ttu-id="ea8cd-112">Bir dosya tanıtıcısı veya bir COM sarmalayıcı gibi bir sistem kaynağı aynı tekniği kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ea8cd-112">You can use this same technique on a system resource such as a file handle or a COM wrapper.</span></span> <span data-ttu-id="ea8cd-113">Kullandığınız bir `Using` engelleme emin olmak için çıkış sonra diğer bileşenleri için kullanılabilir kaynak bırakmak istediğinizde `Using` bloğu.</span><span class="sxs-lookup"><span data-stu-id="ea8cd-113">You use a `Using` block when you want to be sure to leave the resource available for other components after you have exited the `Using` block.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea8cd-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ea8cd-114">See Also</span></span>  
 <xref:System.Data.SqlClient.SqlConnection>  
 [<span data-ttu-id="ea8cd-115">Denetim akışı</span><span class="sxs-lookup"><span data-stu-id="ea8cd-115">Control Flow</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)  
 [<span data-ttu-id="ea8cd-116">Karar yapıları</span><span class="sxs-lookup"><span data-stu-id="ea8cd-116">Decision Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)  
 [<span data-ttu-id="ea8cd-117">Döngü yapıları</span><span class="sxs-lookup"><span data-stu-id="ea8cd-117">Loop Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)  
 [<span data-ttu-id="ea8cd-118">Diğer denetim yapıları</span><span class="sxs-lookup"><span data-stu-id="ea8cd-118">Other Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)  
 [<span data-ttu-id="ea8cd-119">İç içe geçmiş denetim yapıları</span><span class="sxs-lookup"><span data-stu-id="ea8cd-119">Nested Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)  
 [<span data-ttu-id="ea8cd-120">Using deyimi</span><span class="sxs-lookup"><span data-stu-id="ea8cd-120">Using Statement</span></span>](../../../../visual-basic/language-reference/statements/using-statement.md)
