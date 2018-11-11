---
title: ADO.NET bağlantı dizeleri
ms.date: 10/10/2018
ms.assetid: 745c5f95-2f02-4674-b378-6d51a7ec2490
ms.openlocfilehash: 078fdab257115296f9ff00330265cb14ff8674c8
ms.sourcegitcommit: 5fd80619c760fa8c25d33a6f5661247cb65da465
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50409463"
---
# <a name="connection-strings-in-adonet"></a><span data-ttu-id="fd4a8-102">ADO.NET bağlantı dizeleri</span><span class="sxs-lookup"><span data-stu-id="fd4a8-102">Connection Strings in ADO.NET</span></span>

<span data-ttu-id="fd4a8-103">Bir bağlantı dizesi, bir veri kaynağı için veri sağlayıcısı'ndan bir parametre olarak geçen başlatma bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="fd4a8-103">A connection string contains initialization information that is passed as a parameter from a data provider to a data source.</span></span> <span data-ttu-id="fd4a8-104">Veri sağlayıcısı değeri olarak bağlantı dizesini alan <xref:System.Data.Common.DbConnection.ConnectionString?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="fd4a8-104">The data provider receives the connection string as the value of the <xref:System.Data.Common.DbConnection.ConnectionString?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="fd4a8-105">Sağlayıcı bağlantı dizesini ayrıştırmak ve sözdiziminin doğru olduğunu ve anahtar sözcükleri desteklendiğinden emin olmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="fd4a8-105">The provider parses the connection string and ensures that the syntax is correct and that the keywords are supported.</span></span> <span data-ttu-id="fd4a8-106">Ardından <xref:System.Data.Common.DbConnection.Open?displayProperty=nameWithType> yöntemi, veri kaynağına ayrıştırılmış bağlantı parametrelerini geçirir.</span><span class="sxs-lookup"><span data-stu-id="fd4a8-106">Then the <xref:System.Data.Common.DbConnection.Open?displayProperty=nameWithType> method passes the parsed connection parameters to the data source.</span></span> <span data-ttu-id="fd4a8-107">Veri kaynağını daha fazla doğrulama gerçekleştirir ve bir bağlantı kurar.</span><span class="sxs-lookup"><span data-stu-id="fd4a8-107">The data source performs further validation and establishes a connection.</span></span>

## <a name="connection-string-syntax"></a><span data-ttu-id="fd4a8-108">Bağlantı dizesi söz dizimi</span><span class="sxs-lookup"><span data-stu-id="fd4a8-108">Connection string syntax</span></span>

<span data-ttu-id="fd4a8-109">Bir bağlantı dizesi anahtar/değer parametresi çiftleri noktalı virgülle ayrılmış bir listesi verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="fd4a8-109">A connection string is a semicolon-delimited list of key/value parameter pairs:</span></span>
  
    keyword1=value; keyword2=value;
  
<span data-ttu-id="fd4a8-110">Anahtar sözcükler, büyük küçük harfe duyarlı değildir.</span><span class="sxs-lookup"><span data-stu-id="fd4a8-110">Keywords are not case-sensitive.</span></span> <span data-ttu-id="fd4a8-111">Değerleri, ancak veri kaynağına bağlı olarak duyarlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="fd4a8-111">Values, however, may be case-sensitive, depending on the data source.</span></span> <span data-ttu-id="fd4a8-112">Hem anahtar hem de değerleri içerebilir [boşluk karakterleri](https://en.wikipedia.org/wiki/Whitespace_character#Unicode).</span><span class="sxs-lookup"><span data-stu-id="fd4a8-112">Both keywords and values may contain [whitespace characters](https://en.wikipedia.org/wiki/Whitespace_character#Unicode).</span></span> <span data-ttu-id="fd4a8-113">Baştaki ve sondaki boşluk anahtar sözcükleri yok sayıldı ve tırnak işareti olmayan değerler.</span><span class="sxs-lookup"><span data-stu-id="fd4a8-113">Leading and trailing white space is ignored in keywords and unquoted values.</span></span>

<span data-ttu-id="fd4a8-114">Bir değer virgül içeriyorsa [Unicode denetim karakterlerini](https://en.wikipedia.org/wiki/Unicode_control_characters), veya baştaki veya sondaki boşlukları, bunu tek veya çift tırnak içine alınmalıdır.</span><span class="sxs-lookup"><span data-stu-id="fd4a8-114">If a value contains the semicolon, [Unicode control characters](https://en.wikipedia.org/wiki/Unicode_control_characters), or leading or trailing white space, it must be enclosed in single or double quotation marks.</span></span> <span data-ttu-id="fd4a8-115">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="fd4a8-115">For example:</span></span>

    Keyword=" whitespace  ";
    Keyword='special;character';

<span data-ttu-id="fd4a8-116">Kapsayan karakter kendisini kapsayan değeri içinde gerçekleşmeyebilir.</span><span class="sxs-lookup"><span data-stu-id="fd4a8-116">The enclosing character may not occur within the value it encloses.</span></span> <span data-ttu-id="fd4a8-117">Bu nedenle, tek tırnak işareti içeren bir değeri yalnızca çift tırnak işareti bulunan ve tersi içine alınabilir:</span><span class="sxs-lookup"><span data-stu-id="fd4a8-117">Therefore, a value containing single quotation marks can be enclosed only in double quotation marks, and vice versa:</span></span>

    Keyword='double"quotation;mark';
    Keyword="single'quotation;mark";

<span data-ttu-id="fd4a8-118">Aşağıdaki bağlantı dizelerinin geçerli olduğu şekilde eşittir işareti yanı sıra, tırnak işaretleri kaçış, gerek yoktur:</span><span class="sxs-lookup"><span data-stu-id="fd4a8-118">The quotation marks themselves, as well as the equals sign, do not require escaping, so the following connection strings are valid:</span></span>

    Keyword=no "escaping" 'required';
    Keyword=a=b=c

<span data-ttu-id="fd4a8-119">Sonraki noktalı virgül veya dizenin sonuna kadar her değer okunur olduğundan, ikinci örnek değer `a=b=c`, ve son noktalı virgül isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="fd4a8-119">Since each value is read till the next semicolon or the end of string, the value in the latter example is `a=b=c`, and the final semicolon is optional.</span></span>

<span data-ttu-id="fd4a8-120">Tüm bağlantı dizeleri, yukarıda açıklanan aynı temel sözdizimi paylaşın.</span><span class="sxs-lookup"><span data-stu-id="fd4a8-120">All connection strings share the same basic syntax described above.</span></span> <span data-ttu-id="fd4a8-121">Tanınan bir anahtar kümesini sağlayıcısında ancak bağlıdır ve önceki API'leri yıl boyunca gelişmiştir *ODBC*.</span><span class="sxs-lookup"><span data-stu-id="fd4a8-121">The set of recognized keywords depends on the provider, however, and has evolved over the years from earlier APIs such as *ODBC*.</span></span> <span data-ttu-id="fd4a8-122">*.NET Framework* için veri sağlayıcısı *SQL Server* (`SqlClient`) daha eski API'lar, birçok sözcüklerden destekler ancak genellikle daha esnek ve eş anlamlılar pek çok ortak bağlantı dizesini kabul eder. anahtar sözcükler.</span><span class="sxs-lookup"><span data-stu-id="fd4a8-122">The *.NET Framework* data provider for *SQL Server* (`SqlClient`) supports many keywords from older APIs, but is generally more flexible and accepts synonyms for many of the common connection string keywords.</span></span>

<span data-ttu-id="fd4a8-123">Yazım hatalarının hatalara neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="fd4a8-123">Typing mistakes can cause errors.</span></span> <span data-ttu-id="fd4a8-124">Örneğin, `Integrated Security=true` geçerlidir, ancak `IntegratedSecurity=true` bir hataya neden olur.</span><span class="sxs-lookup"><span data-stu-id="fd4a8-124">For example, `Integrated Security=true` is valid, but `IntegratedSecurity=true` causes an error.</span></span>

<span data-ttu-id="fd4a8-125">Bağlantı dizeleri çalışma anında doğrulanmamış kullanıcı girişini el ile oluşturulmuş dize enjeksiyon saldırılarına karşı savunmasız ve veri kaynağındaki güvenliği tehlikeye atabilir.</span><span class="sxs-lookup"><span data-stu-id="fd4a8-125">Connection strings constructed manually at run time from unvalidated user input are vulnerable to string-injection attacks and jeopardize security at the data source.</span></span> <span data-ttu-id="fd4a8-126">Bu sorunları gidermeye yönelik *ADO.NET* 2.0 kullanılmaya [bağlantı dizesi oluşturucular](../../../../docs/framework/data/adonet/connection-string-builders.md) her *.NET Framework* veri sağlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="fd4a8-126">To address these problems, *ADO.NET* 2.0 introduced [connection string builders](../../../../docs/framework/data/adonet/connection-string-builders.md) for each *.NET Framework* data provider.</span></span> <span data-ttu-id="fd4a8-127">Bu bağlantı dizesi oluşturucular parametreleri kesin türü belirtilmiş bir özellik olarak kullanıma sunmak ve veri kaynağına göndermeden önce bağlantı dizesini doğrulamak mümkün kılar.</span><span class="sxs-lookup"><span data-stu-id="fd4a8-127">These connection string builders expose parameters as strongly-typed properties, and make it possible to validate the connection string before it's sent to the data source.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="fd4a8-128">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="fd4a8-128">In This Section</span></span>  
 [<span data-ttu-id="fd4a8-129">Bağlantı Dizesi Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="fd4a8-129">Connection String Builders</span></span>](../../../../docs/framework/data/adonet/connection-string-builders.md)  
 <span data-ttu-id="fd4a8-130">Nasıl kullanılacağını gösteren `ConnectionStringBuilder` sınıfları geçerli bağlantı dizeleri oluşturmak için çalışma zamanında.</span><span class="sxs-lookup"><span data-stu-id="fd4a8-130">Demonstrates how to use the `ConnectionStringBuilder` classes to construct valid connection strings at run time.</span></span>
  
 [<span data-ttu-id="fd4a8-131">Bağlantı Dizeleri ve Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="fd4a8-131">Connection Strings and Configuration Files</span></span>](../../../../docs/framework/data/adonet/connection-strings-and-configuration-files.md)  
 <span data-ttu-id="fd4a8-132">Bağlantı dizelerini yapılandırma dosyalarında depolanıp gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="fd4a8-132">Demonstrates how to store and retrieve connection strings in configuration files.</span></span>
  
 [<span data-ttu-id="fd4a8-133">Bağlantı Dizesi Söz Dizimi</span><span class="sxs-lookup"><span data-stu-id="fd4a8-133">Connection String Syntax</span></span>](../../../../docs/framework/data/adonet/connection-string-syntax.md)  
 <span data-ttu-id="fd4a8-134">Sağlayıcıya özgü bağlantı dizeleri için yapılandırmayı açıklar `SqlClient`, `OracleClient`, `OleDb`, ve `Odbc`.</span><span class="sxs-lookup"><span data-stu-id="fd4a8-134">Describes how to configure provider-specific connection strings for `SqlClient`, `OracleClient`, `OleDb`, and `Odbc`.</span></span>
  
 [<span data-ttu-id="fd4a8-135">Bağlantı Bilgilerini Koruma</span><span class="sxs-lookup"><span data-stu-id="fd4a8-135">Protecting Connection Information</span></span>](../../../../docs/framework/data/adonet/protecting-connection-information.md)  
 <span data-ttu-id="fd4a8-136">Bir veri kaynağına bağlanmak için kullanılan bilgileri korumaya yönelik teknikleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="fd4a8-136">Demonstrates techniques for protecting information used to connect to a data source.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="fd4a8-137">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fd4a8-137">See Also</span></span>  
 [<span data-ttu-id="fd4a8-138">Veri Kaynağına Bağlanma</span><span class="sxs-lookup"><span data-stu-id="fd4a8-138">Connecting to a Data Source</span></span>](/cpp/data/odbc/connecting-to-a-data-source)  
 [<span data-ttu-id="fd4a8-139">ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="fd4a8-139">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
