---
title: Bağlam Bağlantısı
ms.date: 03/30/2017
ms.assetid: e443ca86-9243-4234-a822-ed10a53a9de0
ms.openlocfilehash: 85b303d62b619a8139ca56b23cacd3411cebc17b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91188856"
---
# <a name="the-context-connection"></a><span data-ttu-id="57ae4-102">Bağlam Bağlantısı</span><span class="sxs-lookup"><span data-stu-id="57ae4-102">The Context Connection</span></span>

<span data-ttu-id="57ae4-103">İç veri erişimi sorunu oldukça yaygın bir senaryodur.</span><span class="sxs-lookup"><span data-stu-id="57ae4-103">The problem of internal data access is a fairly common scenario.</span></span> <span data-ttu-id="57ae4-104">Diğer bir deyişle, ortak dil çalışma zamanı (CLR) saklı yordamının veya işlevinin yürütüldüğü aynı sunucuya erişmek istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="57ae4-104">That is, you wish to access the same server on which your common language runtime (CLR) stored procedure or function is executing.</span></span> <span data-ttu-id="57ae4-105">Bir seçenek, kullanarak bağlantı oluşturmak <xref:System.Data.SqlClient.SqlConnection> , yerel sunucuya işaret eden bir bağlantı dizesi belirtmek ve bağlantıyı açmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="57ae4-105">One option is to create a connection using <xref:System.Data.SqlClient.SqlConnection>, specify a connection string that points to the local server, and open the connection.</span></span> <span data-ttu-id="57ae4-106">Bu, oturum açmak için kimlik bilgilerinin belirtilmesini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="57ae4-106">This requires specifying credentials for logging in.</span></span> <span data-ttu-id="57ae4-107">Bağlantı, saklı yordam veya işlevden farklı bir veritabanı oturumunda, farklı seçeneklere sahip olabilir, bu durum `SET` ayrı bir işlemdir, geçici tablolarınızı göremez ve bu şekilde devam eder.</span><span class="sxs-lookup"><span data-stu-id="57ae4-107">The connection is in a different database session than the stored procedure or function, it may have different `SET` options, it is in a separate transaction, it does not see your temporary tables, and so on.</span></span> <span data-ttu-id="57ae4-108">Yönetilen saklı yordamınız veya işlev kodunuz SQL Server işlemde yürütülürse, bu, birisinin bu sunucuya bağlanması ve bunu çağırmak için bir SQL deyimidir.</span><span class="sxs-lookup"><span data-stu-id="57ae4-108">If your managed stored procedure or function code is executing in the SQL Server process, it is because someone connected to that server and executed a SQL statement to invoke it.</span></span> <span data-ttu-id="57ae4-109">Büyük olasılıkla, saklı yordamın veya işlevin bu bağlantı bağlamında yürütülmesi, işlem, `SET` Seçenekler ve benzeri işlemler yapmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="57ae4-109">You probably want the stored procedure or function to execute in the context of that connection, along with its transaction, `SET` options, and so on.</span></span> <span data-ttu-id="57ae4-110">Bu, bağlam bağlantısı olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="57ae4-110">This is called the context connection.</span></span>  
  
 <span data-ttu-id="57ae4-111">Bağlam bağlantısı, Transact-SQL deyimlerini, kodunuzun ilk yerde çağrıldığı bağlamda yürütmenize imkan tanır.</span><span class="sxs-lookup"><span data-stu-id="57ae4-111">The context connection lets you execute Transact-SQL statements in the same context that your code was invoked in the first place.</span></span> <span data-ttu-id="57ae4-112">Daha ayrıntılı bilgi için, kullanmakta olduğunuz SQL Server sürümü için SQL Server Books Online sürümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="57ae4-112">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="57ae4-113">**SQL Server belgeleri**</span><span class="sxs-lookup"><span data-stu-id="57ae4-113">**SQL Server documentation**</span></span>  
  
1. [<span data-ttu-id="57ae4-114">Bağlam Bağlantısı</span><span class="sxs-lookup"><span data-stu-id="57ae4-114">The Context Connection</span></span>](/sql/relational-databases/clr-integration/data-access/context-connection)  
  
## <a name="see-also"></a><span data-ttu-id="57ae4-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="57ae4-115">See also</span></span>

- [<span data-ttu-id="57ae4-116">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="57ae4-116">ADO.NET Overview</span></span>](../ado-net-overview.md)
