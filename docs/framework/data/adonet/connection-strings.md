---
title: ADO.NET içinde bağlantı dizeleri
ms.date: 10/10/2018
ms.assetid: 745c5f95-2f02-4674-b378-6d51a7ec2490
ms.openlocfilehash: 02fe8d984f1287673477bb142b3f9626e248898e
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/20/2019
ms.locfileid: "68363753"
---
# <a name="connection-strings-in-adonet"></a><span data-ttu-id="42ef3-102">ADO.NET içinde bağlantı dizeleri</span><span class="sxs-lookup"><span data-stu-id="42ef3-102">Connection Strings in ADO.NET</span></span>

<span data-ttu-id="42ef3-103">Bir bağlantı dizesi, veri sağlayıcısından bir veri kaynağına parametre olarak geçirilen başlatma bilgilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="42ef3-103">A connection string contains initialization information that is passed as a parameter from a data provider to a data source.</span></span> <span data-ttu-id="42ef3-104">Veri sağlayıcısı, bağlantı dizesini <xref:System.Data.Common.DbConnection.ConnectionString?displayProperty=nameWithType> özelliğin değeri olarak alır.</span><span class="sxs-lookup"><span data-stu-id="42ef3-104">The data provider receives the connection string as the value of the <xref:System.Data.Common.DbConnection.ConnectionString?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="42ef3-105">Sağlayıcı bağlantı dizesini ayrıştırır ve sözdiziminin doğru olduğundan ve anahtar sözcüklerin desteklendiğinden emin olmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="42ef3-105">The provider parses the connection string and ensures that the syntax is correct and that the keywords are supported.</span></span> <span data-ttu-id="42ef3-106">Daha sonra <xref:System.Data.Common.DbConnection.Open?displayProperty=nameWithType> yöntemi, ayrıştırılmış bağlantı parametrelerini veri kaynağına geçirir.</span><span class="sxs-lookup"><span data-stu-id="42ef3-106">Then the <xref:System.Data.Common.DbConnection.Open?displayProperty=nameWithType> method passes the parsed connection parameters to the data source.</span></span> <span data-ttu-id="42ef3-107">Veri kaynağı daha fazla doğrulama gerçekleştirir ve bir bağlantı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="42ef3-107">The data source performs further validation and establishes a connection.</span></span>

## <a name="connection-string-syntax"></a><span data-ttu-id="42ef3-108">Bağlantı dizesi sözdizimi</span><span class="sxs-lookup"><span data-stu-id="42ef3-108">Connection string syntax</span></span>

<span data-ttu-id="42ef3-109">Bağlantı dizesi, anahtar/değer parametre çiftlerinin noktalı virgülle ayrılmış listesidir:</span><span class="sxs-lookup"><span data-stu-id="42ef3-109">A connection string is a semicolon-delimited list of key/value parameter pairs:</span></span>

```
keyword1=value; keyword2=value;
```

<span data-ttu-id="42ef3-110">Anahtar sözcükler büyük/küçük harfe duyarlı değildir.</span><span class="sxs-lookup"><span data-stu-id="42ef3-110">Keywords are not case-sensitive.</span></span> <span data-ttu-id="42ef3-111">Ancak değerler, veri kaynağına bağlı olarak büyük/küçük harfe duyarlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="42ef3-111">Values, however, may be case-sensitive, depending on the data source.</span></span> <span data-ttu-id="42ef3-112">Anahtar sözcüklerin ve değerlerin her ikisi de [boşluk karakterleri](https://en.wikipedia.org/wiki/Whitespace_character#Unicode)içerebilir.</span><span class="sxs-lookup"><span data-stu-id="42ef3-112">Both keywords and values may contain [whitespace characters](https://en.wikipedia.org/wiki/Whitespace_character#Unicode).</span></span> <span data-ttu-id="42ef3-113">Baştaki ve sondaki boşluk, anahtar sözcüklerde ve tırnak işaretsiz değerlerde yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="42ef3-113">Leading and trailing white space is ignored in keywords and unquoted values.</span></span>

<span data-ttu-id="42ef3-114">Bir değer noktalı virgül, [Unicode denetim karakterleri](https://en.wikipedia.org/wiki/Unicode_control_characters)veya baştaki veya sondaki boşluk içeriyorsa, tek veya çift tırnak işareti içine alınmalıdır.</span><span class="sxs-lookup"><span data-stu-id="42ef3-114">If a value contains the semicolon, [Unicode control characters](https://en.wikipedia.org/wiki/Unicode_control_characters), or leading or trailing white space, it must be enclosed in single or double quotation marks.</span></span> <span data-ttu-id="42ef3-115">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="42ef3-115">For example:</span></span>

```
Keyword=" whitespace  ";
Keyword='special;character';
```

<span data-ttu-id="42ef3-116">Kapsayan karakter, içerdiği değer içinde gerçekleşmeyebilir.</span><span class="sxs-lookup"><span data-stu-id="42ef3-116">The enclosing character may not occur within the value it encloses.</span></span> <span data-ttu-id="42ef3-117">Bu nedenle, tek tırnak işareti içeren bir değer yalnızca çift tırnak işaretleri içine alınabilir ve tam tersi de geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="42ef3-117">Therefore, a value containing single quotation marks can be enclosed only in double quotation marks, and vice versa:</span></span>

```
Keyword='double"quotation;mark';
Keyword="single'quotation;mark";
```

<span data-ttu-id="42ef3-118">Ayrıca, kapsayan karakterden ikisini birlikte kullanarak da kaçış yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="42ef3-118">You can also escape the enclosing character by using two of them together:</span></span>

```
Keyword="double""quotation";
Keyword='single''quotation';
```

<span data-ttu-id="42ef3-119">Tırnak işareti ve eşittir işareti, kaçış gerektirmez, bu nedenle aşağıdaki bağlantı dizeleri geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="42ef3-119">The quotation marks themselves, as well as the equals sign, do not require escaping, so the following connection strings are valid:</span></span>

```
Keyword=no "escaping" 'required';
Keyword=a=b=c
```

<span data-ttu-id="42ef3-120">Her değer bir sonraki noktalı virgül veya dize sonuna kadar okunduğundan, ikinci örnekteki `a=b=c`değer ve son noktalı virgül isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="42ef3-120">Since each value is read till the next semicolon or the end of string, the value in the latter example is `a=b=c`, and the final semicolon is optional.</span></span>

<span data-ttu-id="42ef3-121">Tüm bağlantı dizeleri yukarıda açıklanan temel sözdizimini paylaşır.</span><span class="sxs-lookup"><span data-stu-id="42ef3-121">All connection strings share the same basic syntax described above.</span></span> <span data-ttu-id="42ef3-122">Tanınan anahtar sözcükler kümesi, sağlayıcıya bağlıdır ve *ODBC*gibi önceki API 'lerden yıllarca yaşmıştır.</span><span class="sxs-lookup"><span data-stu-id="42ef3-122">The set of recognized keywords depends on the provider, however, and has evolved over the years from earlier APIs such as *ODBC*.</span></span> <span data-ttu-id="42ef3-123">*SQL Server* (`SqlClient`) için *.NET Framework* veri sağlayıcısı, eski API 'lerden birçok anahtar sözcüğü destekler, ancak genellikle daha esnektir ve ortak bağlantı dizesi anahtar sözcüklerinin birçoğu için eş anlamlıları kabul eder.</span><span class="sxs-lookup"><span data-stu-id="42ef3-123">The *.NET Framework* data provider for *SQL Server* (`SqlClient`) supports many keywords from older APIs, but is generally more flexible and accepts synonyms for many of the common connection string keywords.</span></span>

<span data-ttu-id="42ef3-124">Yazım hataları hatalara neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="42ef3-124">Typing mistakes can cause errors.</span></span> <span data-ttu-id="42ef3-125">Örneğin, `Integrated Security=true` geçerlidir, ancak `IntegratedSecurity=true` hataya neden olur.</span><span class="sxs-lookup"><span data-stu-id="42ef3-125">For example, `Integrated Security=true` is valid, but `IntegratedSecurity=true` causes an error.</span></span>

<span data-ttu-id="42ef3-126">Kimliği doğrulanmamış Kullanıcı girişinden, çalışma zamanında el ile oluşturulan bağlantı dizeleri, dize ekleme saldırılarına karşı savunmasız kalır ve veri kaynağındaki güvenliği tehlikeye at.</span><span class="sxs-lookup"><span data-stu-id="42ef3-126">Connection strings constructed manually at run time from unvalidated user input are vulnerable to string-injection attacks and jeopardize security at the data source.</span></span> <span data-ttu-id="42ef3-127">Bu sorunları gidermek için, *ADO.NET* 2,0 her bir *.NET Framework* veri sağlayıcısı için [bağlantı dizesi oluşturucuları](../../../../docs/framework/data/adonet/connection-string-builders.md) sunmuştur.</span><span class="sxs-lookup"><span data-stu-id="42ef3-127">To address these problems, *ADO.NET* 2.0 introduced [connection string builders](../../../../docs/framework/data/adonet/connection-string-builders.md) for each *.NET Framework* data provider.</span></span> <span data-ttu-id="42ef3-128">Bu bağlantı dizesi oluşturucuları, parametreleri kesin türü belirtilmiş özellikler olarak kullanıma sunar ve veri kaynağına gönderilmeden önce bağlantı dizesinin doğrulanmasını mümkün hale getirir.</span><span class="sxs-lookup"><span data-stu-id="42ef3-128">These connection string builders expose parameters as strongly-typed properties, and make it possible to validate the connection string before it's sent to the data source.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="42ef3-129">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="42ef3-129">In This Section</span></span>

<span data-ttu-id="42ef3-130">[Bağlantı dizesi oluşturucuları](../../../../docs/framework/data/adonet/connection-string-builders.md)</span><span class="sxs-lookup"><span data-stu-id="42ef3-130">[Connection String Builders](../../../../docs/framework/data/adonet/connection-string-builders.md)</span></span>\
<span data-ttu-id="42ef3-131">Çalışma zamanında geçerli bağlantı dizeleri `ConnectionStringBuilder` oluşturmak için sınıfların nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="42ef3-131">Demonstrates how to use the `ConnectionStringBuilder` classes to construct valid connection strings at run time.</span></span>

<span data-ttu-id="42ef3-132">[Bağlantı dizeleri ve yapılandırma dosyaları](../../../../docs/framework/data/adonet/connection-strings-and-configuration-files.md)</span><span class="sxs-lookup"><span data-stu-id="42ef3-132">[Connection Strings and Configuration Files](../../../../docs/framework/data/adonet/connection-strings-and-configuration-files.md)</span></span>\
<span data-ttu-id="42ef3-133">Yapılandırma dosyalarındaki bağlantı dizelerinin nasıl depolanacağını ve alınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="42ef3-133">Demonstrates how to store and retrieve connection strings in configuration files.</span></span>

<span data-ttu-id="42ef3-134">[Bağlantı dizesi sözdizimi](../../../../docs/framework/data/adonet/connection-string-syntax.md)</span><span class="sxs-lookup"><span data-stu-id="42ef3-134">[Connection String Syntax](../../../../docs/framework/data/adonet/connection-string-syntax.md)</span></span>\
<span data-ttu-id="42ef3-135">, `SqlClient`, Ve `OracleClient` `OleDb`için sağlayıcıyaözelbağlantıdizelerininnasılyapılandırılacağınıaçıklar.`Odbc`</span><span class="sxs-lookup"><span data-stu-id="42ef3-135">Describes how to configure provider-specific connection strings for `SqlClient`, `OracleClient`, `OleDb`, and `Odbc`.</span></span>

<span data-ttu-id="42ef3-136">[Bağlantı bilgilerini koruma](../../../../docs/framework/data/adonet/protecting-connection-information.md)</span><span class="sxs-lookup"><span data-stu-id="42ef3-136">[Protecting Connection Information](../../../../docs/framework/data/adonet/protecting-connection-information.md)</span></span>\
<span data-ttu-id="42ef3-137">Bir veri kaynağına bağlanmak için kullanılan bilgileri koruma tekniklerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="42ef3-137">Demonstrates techniques for protecting information used to connect to a data source.</span></span>

## <a name="see-also"></a><span data-ttu-id="42ef3-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="42ef3-138">See also</span></span>

- [<span data-ttu-id="42ef3-139">Veri Kaynağına Bağlanma</span><span class="sxs-lookup"><span data-stu-id="42ef3-139">Connecting to a Data Source</span></span>](/cpp/data/odbc/connecting-to-a-data-source)
- [<span data-ttu-id="42ef3-140">ADO.NET yönetilen sağlayıcılar ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="42ef3-140">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
