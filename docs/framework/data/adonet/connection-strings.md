---
title: ADO.NET bağlantı dizeleri
ms.date: 03/30/2017
ms.assetid: 745c5f95-2f02-4674-b378-6d51a7ec2490
ms.openlocfilehash: 1e6e2b6870195c99279639e1f4576a30b7126d4d
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48029404"
---
# <a name="connection-strings-in-adonet"></a><span data-ttu-id="3dba8-102">ADO.NET bağlantı dizeleri</span><span class="sxs-lookup"><span data-stu-id="3dba8-102">Connection Strings in ADO.NET</span></span>
<span data-ttu-id="3dba8-103">.NET Framework 2.0 sunulan geçerli bağlantı dizeleri çalışma zamanında oluşturma kolaylaştırmak bağlantı dizesi Oluşturucusu sınıfları yeni anahtar sözcüklerin Tanıtımı da dahil olmak üzere, bağlantı dizeleri ile çalışmak için yeni özellikler.</span><span class="sxs-lookup"><span data-stu-id="3dba8-103">The .NET Framework 2.0 introduced new capabilities for working with connection strings, including the introduction of new keywords to the connection string builder classes, which facilitate creating valid connection strings at run time.</span></span>  
  
<span data-ttu-id="3dba8-104">Bir bağlantı dizesi, bir veri kaynağı için veri sağlayıcısı'ndan bir parametre olarak geçen başlatma bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="3dba8-104">A connection string contains initialization information that is passed as a parameter from a data provider to a data source.</span></span> <span data-ttu-id="3dba8-105">Veri sağlayıcısında söz dizimi bağlıdır ve bağlantı dizesini bağlantı denemesi sırasında ayrıştırılır.</span><span class="sxs-lookup"><span data-stu-id="3dba8-105">The syntax depends on the data provider, and the connection string is parsed during the attempt to open a connection.</span></span> <span data-ttu-id="3dba8-106">Söz dizimi hataları bir çalışma zamanı özel durumu oluşturur, ancak yalnızca veri kaynağı bağlantı bilgileri aldıktan sonra diğer hataları oluşur.</span><span class="sxs-lookup"><span data-stu-id="3dba8-106">Syntax errors generate a run-time exception, but other errors occur only after the data source receives connection information.</span></span> <span data-ttu-id="3dba8-107">Doğrulanmış sonra veri kaynağının bağlantı dizesinde belirtilen seçenekleri uygular ve bağlantı açar.</span><span class="sxs-lookup"><span data-stu-id="3dba8-107">Once validated, the data source applies the options specified in the connection string and opens the connection.</span></span>
  
<span data-ttu-id="3dba8-108">Bir bağlantı dizesi biçimi, anahtar/değer parametresi çiftleri noktalı virgülle ayrılmış bir listesi verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="3dba8-108">The format of a connection string is a semicolon-delimited list of key/value parameter pairs:</span></span>
  
    keyword1=value; keyword2=value;
  
<span data-ttu-id="3dba8-109">Anahtar sözcükler, büyük küçük harfe duyarlı değildir.</span><span class="sxs-lookup"><span data-stu-id="3dba8-109">Keywords are not case-sensitive.</span></span> <span data-ttu-id="3dba8-110">Değerleri, ancak veri kaynağına bağlı olarak duyarlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="3dba8-110">Values, however, may be case-sensitive, depending on the data source.</span></span> <span data-ttu-id="3dba8-111">Hem anahtar hem de değerleri içerebilir [boşluk karakterleri](https://en.wikipedia.org/wiki/Whitespace_character#Unicode), baştaki ve sondaki anahtar sözcükleri yok sayıldı ve tırnak işareti olmayan olsa da değerler.</span><span class="sxs-lookup"><span data-stu-id="3dba8-111">Both keywords and values may contain [whitespace characters](https://en.wikipedia.org/wiki/Whitespace_character#Unicode), although leading and trailing whitespace is ignored in keywords and unquoted values.</span></span>

<span data-ttu-id="3dba8-112">Bir değer virgül içeriyorsa [Unicode denetim karakterlerini](https://en.wikipedia.org/wiki/Unicode_control_characters), baştaki veya sondaki bu alınmalıdır tek veya çift tırnak işaretleri içine, örneğin:</span><span class="sxs-lookup"><span data-stu-id="3dba8-112">If a value contains the semicolon, [Unicode control characters](https://en.wikipedia.org/wiki/Unicode_control_characters), leading or trailing whitespace it must be enclosed in single or double quotation marks, e.g.:</span></span>

    Keyword=" whitespace  ";
    Keyword='special;character';

<span data-ttu-id="3dba8-113">Kapsayan karakter kendisini kapsayan değeri içinde gerçekleşmeyebilir.</span><span class="sxs-lookup"><span data-stu-id="3dba8-113">The enclosing character may not occur within the value it encloses.</span></span> <span data-ttu-id="3dba8-114">Bu nedenle, tek tırnak işareti içeren bir değeri yalnızca çift tırnak işareti ve bunun tersi de içine alınabilir:</span><span class="sxs-lookup"><span data-stu-id="3dba8-114">Therefore, a value containing single quotation marks can be enclosed only in double quotation marks and vice versa:</span></span>

    Keyword='double"quotation;mark';
    Keyword="single'quotation;mark";

<span data-ttu-id="3dba8-115">Aşağıdaki bağlantı dizelerinin geçerli olduğu şekilde eşittir işareti yanı sıra, tırnak işaretleri kaçış, gerek yoktur:</span><span class="sxs-lookup"><span data-stu-id="3dba8-115">The quotation marks themselves, as well as the equals sign, do not require escaping, so the following connection strings are valid:</span></span>

    Keyword=no "escaping" 'required';
    Keyword=a=b=c

<span data-ttu-id="3dba8-116">Sonraki noktalı virgül veya dizenin sonuna kadar her değer okunur olduğundan, ikinci örnek değer `a=b=c`, ve son noktalı virgül isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="3dba8-116">Since each value is read till the next semicolon or the end of string, the value in the latter example is `a=b=c`, and the final semicolon is optional.</span></span>

<span data-ttu-id="3dba8-117">Geçerli bağlantı dizesi söz dizimi sağlayıcısına bağımlıdır ve ODBC gibi önceki API'leri yıl boyunca gelişmiştir.</span><span class="sxs-lookup"><span data-stu-id="3dba8-117">Valid connection string syntax depends on the provider, and has evolved over the years from earlier APIs like ODBC.</span></span> <span data-ttu-id="3dba8-118">SQL Server (SqlClient) için .NET Framework veri sağlayıcısı birçok eski sözdizimi öğeleri birleştirir ve ortak bağlantı dizesi söz dizimi ile genellikle daha esnektir.</span><span class="sxs-lookup"><span data-stu-id="3dba8-118">The .NET Framework Data Provider for SQL Server (SqlClient) incorporates many elements from older syntax and is generally more flexible with common connection string syntax.</span></span> <span data-ttu-id="3dba8-119">Vardır sık eşit bağlantı dizesi söz dizimi öğeleri için geçerli eş anlamlı sözcükler, ancak bazı söz dizimi ve yazım hataları sorunlara neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="3dba8-119">There are frequently equally valid synonyms for connection string syntax elements, but some syntax and spelling errors can cause problems.</span></span> <span data-ttu-id="3dba8-120">Örneğin, "`Integrated Security=true`" geçerlidir, ancak "`IntegratedSecurity=true`" bir hataya neden olur.</span><span class="sxs-lookup"><span data-stu-id="3dba8-120">For example, "`Integrated Security=true`" is valid, whereas "`IntegratedSecurity=true`" causes an error.</span></span> <span data-ttu-id="3dba8-121">Ayrıca, bağlantı dizeleri çalışma zamanında doğrulanmamış kullanıcı girişini öğesinden oluşturulan dize ekleme saldırılarına karşı veri kaynağında güvenliği tehlikeye yol açabilir.</span><span class="sxs-lookup"><span data-stu-id="3dba8-121">In addition, connection strings constructed at run time from unvalidated user input can lead to string injection attacks, jeopardizing security at the data source.</span></span>
  
<span data-ttu-id="3dba8-122">Bu sorunları gidermeye yönelik her .NET Framework veri sağlayıcısı için yeni bir bağlantı dizesi oluşturucular ADO.NET 2.0 kullanılmaya başlandı.</span><span class="sxs-lookup"><span data-stu-id="3dba8-122">To address these problems, ADO.NET 2.0 introduced new connection string builders for each .NET Framework data provider.</span></span> <span data-ttu-id="3dba8-123">Anahtar sözcükler, özellikleri, veri kaynağına göndermeden önce doğrulanması bağlantı dizesi söz dizimi etkinleştirme olarak sunulur.</span><span class="sxs-lookup"><span data-stu-id="3dba8-123">Keywords are exposed as properties, enabling connection string syntax to be validated before submission to the data source.</span></span>
  
## <a name="in-this-section"></a><span data-ttu-id="3dba8-124">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="3dba8-124">In This Section</span></span>  
 [<span data-ttu-id="3dba8-125">Bağlantı Dizesi Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="3dba8-125">Connection String Builders</span></span>](../../../../docs/framework/data/adonet/connection-string-builders.md)  
 <span data-ttu-id="3dba8-126">Nasıl kullanılacağını gösteren `ConnectionStringBuilder` sınıfları geçerli bağlantı dizeleri oluşturmak için çalışma zamanında.</span><span class="sxs-lookup"><span data-stu-id="3dba8-126">Demonstrates how to use the `ConnectionStringBuilder` classes to construct valid connection strings at run time.</span></span>
  
 [<span data-ttu-id="3dba8-127">Bağlantı Dizeleri ve Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="3dba8-127">Connection Strings and Configuration Files</span></span>](../../../../docs/framework/data/adonet/connection-strings-and-configuration-files.md)  
 <span data-ttu-id="3dba8-128">Bağlantı dizelerini yapılandırma dosyalarında depolanıp gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="3dba8-128">Demonstrates how to store and retrieve connection strings in configuration files.</span></span>
  
 [<span data-ttu-id="3dba8-129">Bağlantı Dizesi Söz Dizimi</span><span class="sxs-lookup"><span data-stu-id="3dba8-129">Connection String Syntax</span></span>](../../../../docs/framework/data/adonet/connection-string-syntax.md)  
 <span data-ttu-id="3dba8-130">Sağlayıcıya özgü bağlantı dizeleri için yapılandırmayı açıklar `SqlClient`, `OracleClient`, `OleDb`, ve `Odbc`.</span><span class="sxs-lookup"><span data-stu-id="3dba8-130">Describes how to configure provider-specific connection strings for `SqlClient`, `OracleClient`, `OleDb`, and `Odbc`.</span></span>
  
 [<span data-ttu-id="3dba8-131">Bağlantı Bilgilerini Koruma</span><span class="sxs-lookup"><span data-stu-id="3dba8-131">Protecting Connection Information</span></span>](../../../../docs/framework/data/adonet/protecting-connection-information.md)  
 <span data-ttu-id="3dba8-132">Bir veri kaynağına bağlanmak için kullanılan bilgileri korumaya yönelik teknikleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="3dba8-132">Demonstrates techniques for protecting information used to connect to a data source.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="3dba8-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3dba8-133">See Also</span></span>  
 [<span data-ttu-id="3dba8-134">Veri Kaynağına Bağlanma</span><span class="sxs-lookup"><span data-stu-id="3dba8-134">Connecting to a Data Source</span></span>](/cpp/data/odbc/connecting-to-a-data-source)  
 [<span data-ttu-id="3dba8-135">ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="3dba8-135">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
