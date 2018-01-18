---
title: "ADO.NET bağlantı dizeleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 745c5f95-2f02-4674-b378-6d51a7ec2490
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 6737b451a0ccb42dfb83dda487e351a9fafde398
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="connection-strings-in-adonet"></a><span data-ttu-id="2fbb8-102">ADO.NET bağlantı dizeleri</span><span class="sxs-lookup"><span data-stu-id="2fbb8-102">Connection Strings in ADO.NET</span></span>
<span data-ttu-id="2fbb8-103">.NET Framework 2.0 bağlantı dizeleri, yeni anahtar sözcüklerin giriş geçerli bir bağlantı dizeleri çalışma zamanında oluşturma kolaylaştırmak bağlantı dizesi Oluşturucu sınıflarına dahil olmak üzere ile çalışmak için yeni özellikler sunar.</span><span class="sxs-lookup"><span data-stu-id="2fbb8-103">The .NET Framework 2.0 introduced new capabilities for working with connection strings, including the introduction of new keywords to the connection string builder classes, which facilitate creating valid connection strings at run time.</span></span>  
  
 <span data-ttu-id="2fbb8-104">Bir bağlantı dizesi, parametre olarak bir veri kaynağına veri sağlayıcıdan geçen başlatma bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="2fbb8-104">A connection string contains initialization information that is passed as a parameter from a data provider to a data source.</span></span> <span data-ttu-id="2fbb8-105">Sözdizimi veri sağlayıcısına bağlıdır ve bağlantı dizesini bir bağlantı açmak için girişimi sırasında ayrıştırılır.</span><span class="sxs-lookup"><span data-stu-id="2fbb8-105">The syntax depends on the data provider, and the connection string is parsed during the attempt to open a connection.</span></span> <span data-ttu-id="2fbb8-106">Sözdizimi hataları bir çalışma zamanı özel durum oluşturur, ancak yalnızca veri kaynağı bağlantı bilgilerini aldıktan sonra diğer hataları oluşur.</span><span class="sxs-lookup"><span data-stu-id="2fbb8-106">Syntax errors generate a run-time exception, but other errors occur only after the data source receives connection information.</span></span> <span data-ttu-id="2fbb8-107">Doğrulanmış sonra veri kaynağının bağlantı dizesinde belirtilen seçeneklerini uygular ve bağlantı açar.</span><span class="sxs-lookup"><span data-stu-id="2fbb8-107">Once validated, the data source applies the options specified in the connection string and opens the connection.</span></span>  
  
 <span data-ttu-id="2fbb8-108">Bir bağlantı dizesi biçimi anahtar/değer parametresi çifti noktalı virgülle ayrılmış bir listesi verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="2fbb8-108">The format of a connection string is a semicolon-delimited list of key/value parameter pairs:</span></span>  
  
 `keyword1=value; keyword2=value;`  
  
 <span data-ttu-id="2fbb8-109">Anahtar sözcükler büyük küçük harfe duyarlı değildir ve anahtar/değer çiftleri arasındaki boşluklar yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="2fbb8-109">Keywords are not case sensitive, and spaces between key/value pairs are ignored.</span></span> <span data-ttu-id="2fbb8-110">Ancak, değerleri büyük veri kaynağı bağlı olarak küçük harf duyarlı, olabilir.</span><span class="sxs-lookup"><span data-stu-id="2fbb8-110">However, values may be case sensitive, depending on the data source.</span></span> <span data-ttu-id="2fbb8-111">Noktalı virgül içeren herhangi bir değer tek tırnak işareti ya da çift tırnak işaretleri çift tırnak içine alınmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2fbb8-111">Any values containing a semicolon, single quotation marks, or double quotation marks must be enclosed in double quotation marks.</span></span>  
  
 <span data-ttu-id="2fbb8-112">Geçerli bağlantı dizesi sözdizimi sağlayıcısına bağlıdır ve ODBC gibi önceki API'leri yıl üzerinden gelişmiştir.</span><span class="sxs-lookup"><span data-stu-id="2fbb8-112">Valid connection string syntax depends on the provider, and has evolved over the years from earlier APIs like ODBC.</span></span> <span data-ttu-id="2fbb8-113">SQL Server (SqlClient) için .NET Framework veri sağlayıcısı eski sözdizimi birçok öğelerini bir araya getirir ve ortak bağlantı dizesi sözdizimi genellikle daha esnektir.</span><span class="sxs-lookup"><span data-stu-id="2fbb8-113">The .NET Framework Data Provider for SQL Server (SqlClient) incorporates many elements from older syntax and is generally more flexible with common connection string syntax.</span></span> <span data-ttu-id="2fbb8-114">Yoktur sık eşit bağlantı dizesi söz dizimi öğeleri için geçerli eş anlamlı sözcükleri, ancak bazı sözdizimi ve yazım hatalarını sorunlara neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="2fbb8-114">There are frequently equally valid synonyms for connection string syntax elements, but some syntax and spelling errors can cause problems.</span></span> <span data-ttu-id="2fbb8-115">Örneğin, "`Integrated Security=true`" geçerlidir, ancak "`IntegratedSecurity=true`" bir hataya neden olur.</span><span class="sxs-lookup"><span data-stu-id="2fbb8-115">For example, "`Integrated Security=true`" is valid, whereas "`IntegratedSecurity=true`" causes an error.</span></span> <span data-ttu-id="2fbb8-116">Ayrıca, doğrulanmamış kullanıcı girişini gelen çalışma zamanında oluşturulan bağlantı dizeleri dize ekleme saldırıları, veri kaynağında güvenliği tehlikeye yol açabilir.</span><span class="sxs-lookup"><span data-stu-id="2fbb8-116">In addition, connection strings constructed at run time from unvalidated user input can lead to string injection attacks, jeopardizing security at the data source.</span></span>  
  
 <span data-ttu-id="2fbb8-117">Bu sorunları gidermek için her .NET Framework veri sağlayıcısı için yeni bağlantı dizesi oluşturucular ADO.NET 2.0 kullanıma sunuldu.</span><span class="sxs-lookup"><span data-stu-id="2fbb8-117">To address these problems, ADO.NET 2.0 introduced new connection string builders for each .NET Framework data provider.</span></span> <span data-ttu-id="2fbb8-118">Anahtar sözcükler, özellikleri, veri kaynağına gönderilmesinden önce doğrulanacak bağlantı dizesi sözdizimi etkinleştirme olarak sunulur.</span><span class="sxs-lookup"><span data-stu-id="2fbb8-118">Keywords are exposed as properties, enabling connection string syntax to be validated before submission to the data source.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2fbb8-119">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="2fbb8-119">In This Section</span></span>  
 [<span data-ttu-id="2fbb8-120">Bağlantı Dizesi Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="2fbb8-120">Connection String Builders</span></span>](../../../../docs/framework/data/adonet/connection-string-builders.md)  
 <span data-ttu-id="2fbb8-121">Nasıl kullanılacağı ortaya `ConnectionStringBuilder` sınıfları geçerli bağlantı dizeleri oluşturmak için çalışma süresi.</span><span class="sxs-lookup"><span data-stu-id="2fbb8-121">Demonstrates how to use the `ConnectionStringBuilder` classes to construct valid connection strings at run time.</span></span>  
  
 [<span data-ttu-id="2fbb8-122">Bağlantı Dizeleri ve Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="2fbb8-122">Connection Strings and Configuration Files</span></span>](../../../../docs/framework/data/adonet/connection-strings-and-configuration-files.md)  
 <span data-ttu-id="2fbb8-123">Bağlantı dizelerini yapılandırma dosyalarında depolanıp gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="2fbb8-123">Demonstrates how to store and retrieve connection strings in configuration files.</span></span>  
  
 [<span data-ttu-id="2fbb8-124">Bağlantı Dizesi Söz Dizimi</span><span class="sxs-lookup"><span data-stu-id="2fbb8-124">Connection String Syntax</span></span>](../../../../docs/framework/data/adonet/connection-string-syntax.md)  
 <span data-ttu-id="2fbb8-125">Sağlayıcıya özgü bağlantı dizeleri için yapılandırmayı açıklar `SqlClient`, `OracleClient`, `OleDb`, ve `Odbc`.</span><span class="sxs-lookup"><span data-stu-id="2fbb8-125">Describes how to configure provider-specific connection strings for `SqlClient`, `OracleClient`, `OleDb`, and `Odbc`.</span></span>  
  
 [<span data-ttu-id="2fbb8-126">Bağlantı Bilgilerini Koruma</span><span class="sxs-lookup"><span data-stu-id="2fbb8-126">Protecting Connection Information</span></span>](../../../../docs/framework/data/adonet/protecting-connection-information.md)  
 <span data-ttu-id="2fbb8-127">Bir veri kaynağına bağlanmak için kullanılan bilgiler koruyan tekniklerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="2fbb8-127">Demonstrates techniques for protecting information used to connect to a data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2fbb8-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2fbb8-128">See Also</span></span>  
 [<span data-ttu-id="2fbb8-129">Veri Kaynağına Bağlanma</span><span class="sxs-lookup"><span data-stu-id="2fbb8-129">Connecting to a Data Source</span></span>](/cpp/data/odbc/connecting-to-a-data-source)  
 [<span data-ttu-id="2fbb8-130">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="2fbb8-130">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
