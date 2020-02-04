---
title: Bağlantı Dizeleri
ms.date: 10/10/2018
ms.assetid: 745c5f95-2f02-4674-b378-6d51a7ec2490
ms.openlocfilehash: cb0b2831a22f3fe51dd7c5bfbe51e72f266a0003
ms.sourcegitcommit: 19014f9c081ca2ff19652ca12503828db8239d48
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/04/2020
ms.locfileid: "76980242"
---
# <a name="connection-strings-in-adonet"></a><span data-ttu-id="a558f-102">ADO.NET içinde bağlantı dizeleri</span><span class="sxs-lookup"><span data-stu-id="a558f-102">Connection Strings in ADO.NET</span></span>

<span data-ttu-id="a558f-103">Bir bağlantı dizesi, veri sağlayıcısından bir veri kaynağına parametre olarak geçirilen başlatma bilgilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="a558f-103">A connection string contains initialization information that is passed as a parameter from a data provider to a data source.</span></span> <span data-ttu-id="a558f-104">Veri sağlayıcısı, <xref:System.Data.Common.DbConnection.ConnectionString?displayProperty=nameWithType> özelliğinin değeri olarak bağlantı dizesini alır.</span><span class="sxs-lookup"><span data-stu-id="a558f-104">The data provider receives the connection string as the value of the <xref:System.Data.Common.DbConnection.ConnectionString?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="a558f-105">Sağlayıcı bağlantı dizesini ayrıştırır ve sözdiziminin doğru olduğundan ve anahtar sözcüklerin desteklendiğinden emin olmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="a558f-105">The provider parses the connection string and ensures that the syntax is correct and that the keywords are supported.</span></span> <span data-ttu-id="a558f-106"><xref:System.Data.Common.DbConnection.Open?displayProperty=nameWithType> yöntemi, ayrıştırılmış bağlantı parametrelerini veri kaynağına geçirir.</span><span class="sxs-lookup"><span data-stu-id="a558f-106">Then the <xref:System.Data.Common.DbConnection.Open?displayProperty=nameWithType> method passes the parsed connection parameters to the data source.</span></span> <span data-ttu-id="a558f-107">Veri kaynağı daha fazla doğrulama gerçekleştirir ve bir bağlantı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a558f-107">The data source performs further validation and establishes a connection.</span></span>

## <a name="connection-string-syntax"></a><span data-ttu-id="a558f-108">Bağlantı dizesi sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a558f-108">Connection string syntax</span></span>

<span data-ttu-id="a558f-109">Bağlantı dizesi, anahtar/değer parametre çiftlerinin noktalı virgülle ayrılmış listesidir:</span><span class="sxs-lookup"><span data-stu-id="a558f-109">A connection string is a semicolon-delimited list of key/value parameter pairs:</span></span>

```csharp
keyword1=value; keyword2=value;
```

<span data-ttu-id="a558f-110">Anahtar sözcükler büyük/küçük harfe duyarlı değildir.</span><span class="sxs-lookup"><span data-stu-id="a558f-110">Keywords are not case-sensitive.</span></span> <span data-ttu-id="a558f-111">Ancak değerler, veri kaynağına bağlı olarak büyük/küçük harfe duyarlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="a558f-111">Values, however, may be case-sensitive, depending on the data source.</span></span> <span data-ttu-id="a558f-112">Anahtar sözcüklerin ve değerlerin her ikisi de [boşluk karakterleri](https://en.wikipedia.org/wiki/Whitespace_character#Unicode)içerebilir.</span><span class="sxs-lookup"><span data-stu-id="a558f-112">Both keywords and values may contain [whitespace characters](https://en.wikipedia.org/wiki/Whitespace_character#Unicode).</span></span> <span data-ttu-id="a558f-113">Baştaki ve sondaki boşluk, anahtar sözcüklerde ve tırnak işaretsiz değerlerde yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="a558f-113">Leading and trailing white space is ignored in keywords and unquoted values.</span></span>

<span data-ttu-id="a558f-114">Bir değer noktalı virgül, [Unicode denetim karakterleri](https://en.wikipedia.org/wiki/Unicode_control_characters)veya baştaki veya sondaki boşluk içeriyorsa, tek veya çift tırnak işareti içine alınmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a558f-114">If a value contains the semicolon, [Unicode control characters](https://en.wikipedia.org/wiki/Unicode_control_characters), or leading or trailing white space, it must be enclosed in single or double quotation marks.</span></span> <span data-ttu-id="a558f-115">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="a558f-115">For example:</span></span>

```csharp
Keyword=" whitespace  ";
Keyword='special;character';
```

<span data-ttu-id="a558f-116">Kapsayan karakter, içerdiği değer içinde gerçekleşmeyebilir.</span><span class="sxs-lookup"><span data-stu-id="a558f-116">The enclosing character may not occur within the value it encloses.</span></span> <span data-ttu-id="a558f-117">Bu nedenle, tek tırnak işareti içeren bir değer yalnızca çift tırnak işaretleri içine alınabilir ve tam tersi de geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="a558f-117">Therefore, a value containing single quotation marks can be enclosed only in double quotation marks, and vice versa:</span></span>

```csharp
Keyword='double"quotation;mark';
Keyword="single'quotation;mark";
```

<span data-ttu-id="a558f-118">Ayrıca, kapsayan karakterden ikisini birlikte kullanarak da kaçış yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="a558f-118">You can also escape the enclosing character by using two of them together:</span></span>

```csharp
Keyword="double""quotation";
Keyword='single''quotation';
```

<span data-ttu-id="a558f-119">Tırnak işareti ve eşittir işareti, kaçış gerektirmez, bu nedenle aşağıdaki bağlantı dizeleri geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="a558f-119">The quotation marks themselves, as well as the equals sign, do not require escaping, so the following connection strings are valid:</span></span>

```csharp
Keyword=no "escaping" 'required';
Keyword=a=b=c
```

<span data-ttu-id="a558f-120">Her değer bir sonraki noktalı virgül veya dize sonuna kadar okunduğundan, ikinci örnekteki değer `a=b=c`ve son noktalı virgül isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="a558f-120">Since each value is read till the next semicolon or the end of string, the value in the latter example is `a=b=c`, and the final semicolon is optional.</span></span>

<span data-ttu-id="a558f-121">Tüm bağlantı dizeleri yukarıda açıklanan temel sözdizimini paylaşır.</span><span class="sxs-lookup"><span data-stu-id="a558f-121">All connection strings share the same basic syntax described above.</span></span> <span data-ttu-id="a558f-122">Tanınan anahtar sözcükler kümesi, sağlayıcıya bağlıdır ve *ODBC*gibi önceki API 'lerden yıllarca yaşmıştır.</span><span class="sxs-lookup"><span data-stu-id="a558f-122">The set of recognized keywords depends on the provider, however, and has evolved over the years from earlier APIs such as *ODBC*.</span></span> <span data-ttu-id="a558f-123">*SQL Server* (`SqlClient`) için *.NET Framework* veri sağlayıcısı, eski API 'lerden birçok anahtar sözcüğü destekler, ancak genellikle daha esnektir ve ortak bağlantı dizesi anahtar sözcüklerinin birçoğu için eş anlamlıları kabul eder.</span><span class="sxs-lookup"><span data-stu-id="a558f-123">The *.NET Framework* data provider for *SQL Server* (`SqlClient`) supports many keywords from older APIs, but is generally more flexible and accepts synonyms for many of the common connection string keywords.</span></span>

<span data-ttu-id="a558f-124">Yazım hataları hatalara neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="a558f-124">Typing mistakes can cause errors.</span></span> <span data-ttu-id="a558f-125">Örneğin, `Integrated Security=true` geçerlidir, ancak `IntegratedSecurity=true` bir hataya neden olur.</span><span class="sxs-lookup"><span data-stu-id="a558f-125">For example, `Integrated Security=true` is valid, but `IntegratedSecurity=true` causes an error.</span></span>

<span data-ttu-id="a558f-126">Kimliği doğrulanmamış Kullanıcı girişinden, çalışma zamanında el ile oluşturulan bağlantı dizeleri, dize ekleme saldırılarına karşı savunmasız kalır ve veri kaynağındaki güvenliği tehlikeye at.</span><span class="sxs-lookup"><span data-stu-id="a558f-126">Connection strings constructed manually at run time from unvalidated user input are vulnerable to string-injection attacks and jeopardize security at the data source.</span></span> <span data-ttu-id="a558f-127">Bu sorunları gidermek için, *ADO.NET* 2,0 her bir *.NET Framework* veri sağlayıcısı için [bağlantı dizesi oluşturucuları](connection-string-builders.md) sunmuştur.</span><span class="sxs-lookup"><span data-stu-id="a558f-127">To address these problems, *ADO.NET* 2.0 introduced [connection string builders](connection-string-builders.md) for each *.NET Framework* data provider.</span></span> <span data-ttu-id="a558f-128">Bu bağlantı dizesi oluşturucuları, parametreleri kesin türü belirtilmiş özellikler olarak kullanıma sunar ve veri kaynağına gönderilmeden önce bağlantı dizesinin doğrulanmasını mümkün hale getirir.</span><span class="sxs-lookup"><span data-stu-id="a558f-128">These connection string builders expose parameters as strongly-typed properties, and make it possible to validate the connection string before it's sent to the data source.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="a558f-129">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="a558f-129">In This Section</span></span>

<span data-ttu-id="a558f-130">[Bağlantı dizesi oluşturucuları](connection-string-builders.md)</span><span class="sxs-lookup"><span data-stu-id="a558f-130">[Connection String Builders](connection-string-builders.md)</span></span>\
<span data-ttu-id="a558f-131">Çalışma zamanında geçerli bağlantı dizeleri oluşturmak için `ConnectionStringBuilder` sınıflarının nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="a558f-131">Demonstrates how to use the `ConnectionStringBuilder` classes to construct valid connection strings at run time.</span></span>

<span data-ttu-id="a558f-132">[Bağlantı dizeleri ve yapılandırma dosyaları](connection-strings-and-configuration-files.md)</span><span class="sxs-lookup"><span data-stu-id="a558f-132">[Connection Strings and Configuration Files](connection-strings-and-configuration-files.md)</span></span>\
<span data-ttu-id="a558f-133">Yapılandırma dosyalarındaki bağlantı dizelerinin nasıl depolanacağını ve alınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="a558f-133">Demonstrates how to store and retrieve connection strings in configuration files.</span></span>

<span data-ttu-id="a558f-134">[Bağlantı dizesi sözdizimi](connection-string-syntax.md)</span><span class="sxs-lookup"><span data-stu-id="a558f-134">[Connection String Syntax](connection-string-syntax.md)</span></span>\
<span data-ttu-id="a558f-135">`SqlClient`, `OracleClient`, `OleDb`ve `Odbc`için sağlayıcıya özgü bağlantı dizelerinin nasıl yapılandırılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="a558f-135">Describes how to configure provider-specific connection strings for `SqlClient`, `OracleClient`, `OleDb`, and `Odbc`.</span></span>

<span data-ttu-id="a558f-136">[Bağlantı bilgilerini koruma](protecting-connection-information.md)</span><span class="sxs-lookup"><span data-stu-id="a558f-136">[Protecting Connection Information](protecting-connection-information.md)</span></span>\
<span data-ttu-id="a558f-137">Bir veri kaynağına bağlanmak için kullanılan bilgileri koruma tekniklerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="a558f-137">Demonstrates techniques for protecting information used to connect to a data source.</span></span>

## <a name="see-also"></a><span data-ttu-id="a558f-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a558f-138">See also</span></span>

- [<span data-ttu-id="a558f-139">Veri Kaynağına Bağlanma</span><span class="sxs-lookup"><span data-stu-id="a558f-139">Connecting to a Data Source</span></span>](/cpp/data/odbc/connecting-to-a-data-source)
- [<span data-ttu-id="a558f-140">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="a558f-140">ADO.NET Overview</span></span>](ado-net-overview.md)
