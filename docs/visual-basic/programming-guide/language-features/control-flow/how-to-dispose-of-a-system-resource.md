---
description: ': Nasıl yapılır: sistem kaynağını atma (Visual Basic) hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 6594c9e2eedf756cc7a46c2c17deab58fcba3a8c
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100480667"
---
# <a name="how-to-dispose-of-a-system-resource-visual-basic"></a><span data-ttu-id="7082f-103">Nasıl yapılır: Bir Sistem Kaynağını Atma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7082f-103">How to: Dispose of a System Resource (Visual Basic)</span></span>

<span data-ttu-id="7082f-104">`Using`Kodunuzun bloğundan çıkış yaparken sistemin bir kaynağı ortadan kaldırabileceğini güvence altına almak için bir bloğu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7082f-104">You can use a `Using` block to guarantee that the system disposes of a resource when your code exits the block.</span></span> <span data-ttu-id="7082f-105">Bu, büyük miktarda bellek tüketen bir sistem kaynağı kullanıyorsanız veya diğer bileşenlerin de kullanılmasını istiyorsanız kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="7082f-105">This is useful if you are using a system resource that consumes a large amount of memory, or that other components also want to use.</span></span>  
  
### <a name="to-dispose-of-a-database-connection-when-your-code-is-finished-with-it"></a><span data-ttu-id="7082f-106">Kodunuz ile işiniz bittiğinde bir veritabanı bağlantısını atmak için</span><span class="sxs-lookup"><span data-stu-id="7082f-106">To dispose of a database connection when your code is finished with it</span></span>  
  
1. <span data-ttu-id="7082f-107">Kaynak dosyanızın başlangıcında (Bu durumda,) veritabanı bağlantısı için uygun [Içeri aktarmalar ifadesini (.net ad alanı ve türü)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md) eklediğinizden emin olun <xref:System.Data.SqlClient> .</span><span class="sxs-lookup"><span data-stu-id="7082f-107">Make sure you include the appropriate [Imports Statement (.NET Namespace and Type)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md) for the database connection at the beginning of your source file (in this case, <xref:System.Data.SqlClient>).</span></span>  
  
2. <span data-ttu-id="7082f-108">`Using` `Using` Ve deyimleriyle bir blok oluşturun `End Using` .</span><span class="sxs-lookup"><span data-stu-id="7082f-108">Create a `Using` block with the `Using` and `End Using` statements.</span></span> <span data-ttu-id="7082f-109">Bloğun içinde, veritabanı bağlantısıyla ilgilenen kodu koyun.</span><span class="sxs-lookup"><span data-stu-id="7082f-109">Inside the block, put the code that deals with the database connection.</span></span>  
  
3. <span data-ttu-id="7082f-110">Bağlantıyı bildirin ve deyimin bir parçası olarak bir örneğini oluşturun `Using` .</span><span class="sxs-lookup"><span data-stu-id="7082f-110">Declare the connection and create an instance of it as part of the `Using` statement.</span></span>  
  
    ```vb  
    ' Insert the following line at the beginning of your source file.  
    Imports System.Data.SqlClient  
    Public Sub AccessSql(ByVal s As String)  
        Using sqc As New System.Data.SqlClient.SqlConnection(s)  
            MsgBox("Connected with string """ & sqc.ConnectionString & """")  
        End Using  
    End Sub  
    ```  
  
     <span data-ttu-id="7082f-111">İşlenmeyen bir özel durum da dahil olmak üzere bloğundan çıktığınızda sistem kaynağı ortadan kaldırsın.</span><span class="sxs-lookup"><span data-stu-id="7082f-111">The system disposes of the resource no matter how you exit the block, including the case of an unhandled exception.</span></span>  
  
     <span data-ttu-id="7082f-112">`sqc` `Using` Kapsamı bloğuyla sınırlı olduğundan bloğunun dışından erişemediğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="7082f-112">Note that you cannot access `sqc` from outside the `Using` block, because its scope is limited to the block.</span></span>  
  
     <span data-ttu-id="7082f-113">Bu tekniği, bir dosya tanıtıcısı veya bir COM sarmalayıcı gibi bir sistem kaynağı üzerinde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7082f-113">You can use this same technique on a system resource such as a file handle or a COM wrapper.</span></span> <span data-ttu-id="7082f-114">`Using`Bloğundan çıktıktan sonra kaynağı diğer bileşenler için kullanılabilir durumda bırakmaya emin olmak istediğinizde bir blok kullanırsınız `Using` .</span><span class="sxs-lookup"><span data-stu-id="7082f-114">You use a `Using` block when you want to be sure to leave the resource available for other components after you have exited the `Using` block.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7082f-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7082f-115">See also</span></span>

- <xref:System.Data.SqlClient.SqlConnection>
- [<span data-ttu-id="7082f-116">Denetim akışı</span><span class="sxs-lookup"><span data-stu-id="7082f-116">Control Flow</span></span>](index.md)
- [<span data-ttu-id="7082f-117">Karar Yapıları</span><span class="sxs-lookup"><span data-stu-id="7082f-117">Decision Structures</span></span>](decision-structures.md)
- [<span data-ttu-id="7082f-118">Döngü Yapıları</span><span class="sxs-lookup"><span data-stu-id="7082f-118">Loop Structures</span></span>](loop-structures.md)
- [<span data-ttu-id="7082f-119">Diğer Denetim Yapıları</span><span class="sxs-lookup"><span data-stu-id="7082f-119">Other Control Structures</span></span>](other-control-structures.md)
- [<span data-ttu-id="7082f-120">İç İçe Geçmiş Denetim Yapıları</span><span class="sxs-lookup"><span data-stu-id="7082f-120">Nested Control Structures</span></span>](nested-control-structures.md)
- [<span data-ttu-id="7082f-121">Using deyimleri</span><span class="sxs-lookup"><span data-stu-id="7082f-121">Using Statement</span></span>](../../../language-reference/statements/using-statement.md)
