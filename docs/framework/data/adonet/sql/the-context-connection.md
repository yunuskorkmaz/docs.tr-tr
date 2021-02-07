---
description: 'Daha fazla bilgi edinin: bağlam bağlantısı'
title: Bağlam Bağlantısı
ms.date: 03/30/2017
ms.assetid: e443ca86-9243-4234-a822-ed10a53a9de0
ms.openlocfilehash: caea829464ae19a8944f02c4edb38ec41b9bde48
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99767017"
---
# <a name="the-context-connection"></a><span data-ttu-id="72def-103">Bağlam Bağlantısı</span><span class="sxs-lookup"><span data-stu-id="72def-103">The Context Connection</span></span>

<span data-ttu-id="72def-104">İç veri erişimi sorunu oldukça yaygın bir senaryodur.</span><span class="sxs-lookup"><span data-stu-id="72def-104">The problem of internal data access is a fairly common scenario.</span></span> <span data-ttu-id="72def-105">Diğer bir deyişle, ortak dil çalışma zamanı (CLR) saklı yordamının veya işlevinin yürütüldüğü aynı sunucuya erişmek istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="72def-105">That is, you wish to access the same server on which your common language runtime (CLR) stored procedure or function is executing.</span></span> <span data-ttu-id="72def-106">Bir seçenek, kullanarak bağlantı oluşturmak <xref:System.Data.SqlClient.SqlConnection> , yerel sunucuya işaret eden bir bağlantı dizesi belirtmek ve bağlantıyı açmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="72def-106">One option is to create a connection using <xref:System.Data.SqlClient.SqlConnection>, specify a connection string that points to the local server, and open the connection.</span></span> <span data-ttu-id="72def-107">Bu, oturum açmak için kimlik bilgilerinin belirtilmesini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="72def-107">This requires specifying credentials for logging in.</span></span> <span data-ttu-id="72def-108">Bağlantı, saklı yordam veya işlevden farklı bir veritabanı oturumunda, farklı seçeneklere sahip olabilir, bu durum `SET` ayrı bir işlemdir, geçici tablolarınızı göremez ve bu şekilde devam eder.</span><span class="sxs-lookup"><span data-stu-id="72def-108">The connection is in a different database session than the stored procedure or function, it may have different `SET` options, it is in a separate transaction, it does not see your temporary tables, and so on.</span></span> <span data-ttu-id="72def-109">Yönetilen saklı yordamınız veya işlev kodunuz SQL Server işlemde yürütülürse, bu, birisinin bu sunucuya bağlanması ve bunu çağırmak için bir SQL deyimidir.</span><span class="sxs-lookup"><span data-stu-id="72def-109">If your managed stored procedure or function code is executing in the SQL Server process, it is because someone connected to that server and executed a SQL statement to invoke it.</span></span> <span data-ttu-id="72def-110">Büyük olasılıkla, saklı yordamın veya işlevin bu bağlantı bağlamında yürütülmesi, işlem, `SET` Seçenekler ve benzeri işlemler yapmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="72def-110">You probably want the stored procedure or function to execute in the context of that connection, along with its transaction, `SET` options, and so on.</span></span> <span data-ttu-id="72def-111">Bu, bağlam bağlantısı olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="72def-111">This is called the context connection.</span></span>  
  
 <span data-ttu-id="72def-112">Bağlam bağlantısı, Transact-SQL deyimlerini, kodunuzun ilk yerde çağrıldığı bağlamda yürütmenize imkan tanır.</span><span class="sxs-lookup"><span data-stu-id="72def-112">The context connection lets you execute Transact-SQL statements in the same context that your code was invoked in the first place.</span></span> <span data-ttu-id="72def-113">Daha ayrıntılı bilgi için, kullanmakta olduğunuz SQL Server sürümü için SQL Server Books Online sürümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="72def-113">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="72def-114">**SQL Server belgeleri**</span><span class="sxs-lookup"><span data-stu-id="72def-114">**SQL Server documentation**</span></span>  
  
1. [<span data-ttu-id="72def-115">Bağlam Bağlantısı</span><span class="sxs-lookup"><span data-stu-id="72def-115">The Context Connection</span></span>](/sql/relational-databases/clr-integration/data-access/context-connection)  
  
## <a name="see-also"></a><span data-ttu-id="72def-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="72def-116">See also</span></span>

- [<span data-ttu-id="72def-117">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="72def-117">ADO.NET Overview</span></span>](../ado-net-overview.md)
