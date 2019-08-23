---
title: SqlMetal.exe (Kod Üretme Aracı)
ms.date: 03/30/2017
helpviewer_keywords:
- SQLMetal [LINQ to SQL]
- code generation tool
- SQLMetal.exe
- LINQ to SQL, serialization
- LINQ to SQL, DBML files
- LINQ to SQL, SQLMetal
ms.assetid: 819e5a96-7646-4fdb-b14b-fe31221b0614
ms.openlocfilehash: f435c93f68feb564aaca0f52842e567aa688ac64
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69938004"
---
# <a name="sqlmetalexe-code-generation-tool"></a><span data-ttu-id="29762-102">SqlMetal.exe (Kod Üretme Aracı)</span><span class="sxs-lookup"><span data-stu-id="29762-102">SqlMetal.exe (Code Generation Tool)</span></span>
<span data-ttu-id="29762-103">SqlMetal komut satırı aracı .NET Framework [!INCLUDE[vbtecdlinq](../../../includes/vbtecdlinq-md.md)] bileşeni için kod ve eşleme oluşturur.</span><span class="sxs-lookup"><span data-stu-id="29762-103">The SqlMetal command-line tool generates code and mapping for the [!INCLUDE[vbtecdlinq](../../../includes/vbtecdlinq-md.md)] component of the .NET Framework.</span></span> <span data-ttu-id="29762-104">Bu konunun ilerisinde görünen seçenekleri uygulayarak, SqlMetal'den aşağıdakileri içeren çeşitli farklı eylemler gerçekleştirmesini isteyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="29762-104">By applying options that appear later in this topic, you can instruct SqlMetal to perform several different actions that include the following:</span></span>  
  
- <span data-ttu-id="29762-105">Bir veritabanından, kaynak kodu ve eşleme öznitelikleri veya bir eşleme dosyası oluşturmak.</span><span class="sxs-lookup"><span data-stu-id="29762-105">From a database, generate source code and mapping attributes or a mapping file.</span></span>  
  
- <span data-ttu-id="29762-106">Bir veritabanından, dosya özelleştirme için bir ara veritabanı işaretleme dili (.dbml) dosyası oluşturmak.</span><span class="sxs-lookup"><span data-stu-id="29762-106">From a database, generate an intermediate database markup language (.dbml) file for customization.</span></span>  
  
- <span data-ttu-id="29762-107">Bir .dbml dosyasından, kod veya eşleme öznitelikleri veya bir eşleme dosyası üretmek.</span><span class="sxs-lookup"><span data-stu-id="29762-107">From a .dbml file, generate code and mapping attributes or a mapping file.</span></span>  
  
 <span data-ttu-id="29762-108">Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir.</span><span class="sxs-lookup"><span data-stu-id="29762-108">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="29762-109">Varsayılan olarak, dosya şu konumda `drive`bulunur: \Program Files\Microsoft sdks\windows\v \Bin.`n.nn`</span><span class="sxs-lookup"><span data-stu-id="29762-109">By default, the file is located at `drive`:\Program Files\Microsoft SDKs\Windows\v`n.nn`\bin.</span></span> <span data-ttu-id="29762-110">Visual Studio 'Yu yüklemezseniz, [Windows SDK](https://go.microsoft.com/fwlink/?LinkId=142225)Indirerek SqlMetal dosyasını da alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="29762-110">If you do not install Visual Studio, you can also get the SQLMetal file by downloading the [Windows SDK](https://go.microsoft.com/fwlink/?LinkId=142225).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="29762-111">Visual Studio kullanan geliştiriciler de Nesne İlişkisel Tasarımcısı varlık sınıfları oluşturmak için kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="29762-111">Developers who use Visual Studio can also use the Object Relational Designer to generate entity classes.</span></span> <span data-ttu-id="29762-112">Komut satırı yaklaşımı, büyük veritabanları için uygun düşmektedir.</span><span class="sxs-lookup"><span data-stu-id="29762-112">The command-line approach scales well for large databases.</span></span> <span data-ttu-id="29762-113">SqlMetal bir komut satırı aracı olduğundan, bir oluşturma işleminde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="29762-113">Because SqlMetal is a command-line tool, you can use it in a build process.</span></span>  
  
 <span data-ttu-id="29762-114">Aracı çalıştırmak için, Visual Studio için Geliştirici Komut İstemi (veya Windows 7 ' de Visual Studio komut Istemi) kullanın.</span><span class="sxs-lookup"><span data-stu-id="29762-114">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="29762-115">Daha fazla bilgi için bkz. [komut istemleri](../../../docs/framework/tools/developer-command-prompt-for-vs.md). Komut isteminde aşağıdakileri yazın:</span><span class="sxs-lookup"><span data-stu-id="29762-115">For more information, see [Command Prompts](../../../docs/framework/tools/developer-command-prompt-for-vs.md).At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29762-116">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="29762-116">Syntax</span></span>  
  
```  
sqlmetal [options] [<input file>]  
```  
  
## <a name="options"></a><span data-ttu-id="29762-117">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="29762-117">Options</span></span>  
 <span data-ttu-id="29762-118">En güncel seçenek listesini görüntülemek için, yüklü konumdan `sqlmetal /?` bir komut istemine yazın.</span><span class="sxs-lookup"><span data-stu-id="29762-118">To view the most current option list, type `sqlmetal /?` at a command prompt from the installed location.</span></span>  
  
 <span data-ttu-id="29762-119">**Bağlantı seçenekleri**</span><span class="sxs-lookup"><span data-stu-id="29762-119">**Connection Options**</span></span>  
  
|<span data-ttu-id="29762-120">Seçenek</span><span class="sxs-lookup"><span data-stu-id="29762-120">Option</span></span>|<span data-ttu-id="29762-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="29762-121">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="29762-122">**/Server:**  *ad\<>*</span><span class="sxs-lookup"><span data-stu-id="29762-122">**/server:** *\<name>*</span></span>|<span data-ttu-id="29762-123">Veritabanı sunucusu adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="29762-123">Specifies database server name.</span></span>|  
|<span data-ttu-id="29762-124">**/Database:**  *ad\<>*</span><span class="sxs-lookup"><span data-stu-id="29762-124">**/database:** *\<name>*</span></span>|<span data-ttu-id="29762-125">Sunucuda veritabanı kataloğu belirtir.</span><span class="sxs-lookup"><span data-stu-id="29762-125">Specifies database catalog on server.</span></span>|  
|<span data-ttu-id="29762-126">**/User:**  *ad\<>*</span><span class="sxs-lookup"><span data-stu-id="29762-126">**/user:** *\<name>*</span></span>|<span data-ttu-id="29762-127">Oturum açma kullanıcı kimliği belirtir. Varsayılan değer: Windows kimlik doğrulamasını kullanın.</span><span class="sxs-lookup"><span data-stu-id="29762-127">Specifies logon user id. Default value: Use Windows authentication.</span></span>|  
|<span data-ttu-id="29762-128">**/Password:**  *parola\<>*</span><span class="sxs-lookup"><span data-stu-id="29762-128">**/password:** *\<password>*</span></span>|<span data-ttu-id="29762-129">Oturum açma parolasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="29762-129">Specifies logon password.</span></span> <span data-ttu-id="29762-130">Varsayılan değer: Windows kimlik doğrulamasını kullanın.</span><span class="sxs-lookup"><span data-stu-id="29762-130">Default value: Use Windows authentication.</span></span>|  
|<span data-ttu-id="29762-131">**/Conn:**  *bağlantıdizesi\<>*</span><span class="sxs-lookup"><span data-stu-id="29762-131">**/conn:** *\<connection string>*</span></span>|<span data-ttu-id="29762-132">Veritabanı bağlantısı dizesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="29762-132">Specifies database connection string.</span></span> <span data-ttu-id="29762-133">**/Server**, **/Database**, **/User**veya **/Password** seçenekleriyle birlikte kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="29762-133">Cannot be used with **/server**, **/database**, **/user**, or **/password** options.</span></span><br /><br /> <span data-ttu-id="29762-134">Dosya adını bağlantı dizesine eklemeyin.</span><span class="sxs-lookup"><span data-stu-id="29762-134">Do not include the file name in the connection string.</span></span> <span data-ttu-id="29762-135">Bunun yerine, dosya adını giriş dosyası olarak komut satırına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="29762-135">Instead, add the file name to the command line as the input file.</span></span> <span data-ttu-id="29762-136">Örneğin, aşağıdaki satır giriş dosyası olarak "c:\kuzeydoğu WND.mdf" belirtir: **SqlMetal/Code: "c:\Northwind.cs"/Language: CSharp "c:\kuzeydoğu WND.mdf"** .</span><span class="sxs-lookup"><span data-stu-id="29762-136">For example, the following line specifies "c:\northwnd.mdf" as the input file: **sqlmetal /code:"c:\northwind.cs" /language:csharp "c:\northwnd.mdf"**.</span></span>|  
|<span data-ttu-id="29762-137">**/Timeout:**  *saniyeler\<>*</span><span class="sxs-lookup"><span data-stu-id="29762-137">**/timeout:** *\<seconds>*</span></span>|<span data-ttu-id="29762-138">SqlMetal veritabanına eriştiğinde, zaman aşımı değerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="29762-138">Specifies time-out value when SqlMetal accesses the database.</span></span> <span data-ttu-id="29762-139">Varsayılan değer: 0 (yani, zaman sınırı yoktur).</span><span class="sxs-lookup"><span data-stu-id="29762-139">Default value: 0 (that is, no time limit).</span></span>|  
  
 <span data-ttu-id="29762-140">**Ayıklama seçenekleri**</span><span class="sxs-lookup"><span data-stu-id="29762-140">**Extraction options**</span></span>  
  
|<span data-ttu-id="29762-141">Seçenek</span><span class="sxs-lookup"><span data-stu-id="29762-141">Option</span></span>|<span data-ttu-id="29762-142">Açıklama</span><span class="sxs-lookup"><span data-stu-id="29762-142">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="29762-143">**/views**</span><span class="sxs-lookup"><span data-stu-id="29762-143">**/views**</span></span>|<span data-ttu-id="29762-144">Veritabanı görünümlerini ayıklar.</span><span class="sxs-lookup"><span data-stu-id="29762-144">Extracts database views.</span></span>|  
|<span data-ttu-id="29762-145">**/Functions**</span><span class="sxs-lookup"><span data-stu-id="29762-145">**/functions**</span></span>|<span data-ttu-id="29762-146">Veritabanı işlevlerini ayıklar.</span><span class="sxs-lookup"><span data-stu-id="29762-146">Extracts database functions.</span></span>|  
|<span data-ttu-id="29762-147">**/sprocs**</span><span class="sxs-lookup"><span data-stu-id="29762-147">**/sprocs**</span></span>|<span data-ttu-id="29762-148">Saklı yordamları ayıklar.</span><span class="sxs-lookup"><span data-stu-id="29762-148">Extracts stored procedures.</span></span>|  
  
 <span data-ttu-id="29762-149">**Çıkış seçenekleri**</span><span class="sxs-lookup"><span data-stu-id="29762-149">**Output options**</span></span>  
  
|<span data-ttu-id="29762-150">Seçenek</span><span class="sxs-lookup"><span data-stu-id="29762-150">Option</span></span>|<span data-ttu-id="29762-151">Açıklama</span><span class="sxs-lookup"><span data-stu-id="29762-151">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="29762-152">**/DBML** *[: dosya]*</span><span class="sxs-lookup"><span data-stu-id="29762-152">**/dbml** *[:file]*</span></span>|<span data-ttu-id="29762-153">Çıkışı .dbml olarak gönderir.</span><span class="sxs-lookup"><span data-stu-id="29762-153">Sends output as .dbml.</span></span> <span data-ttu-id="29762-154">**/Map** seçeneğiyle birlikte kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="29762-154">Cannot be used with **/map** option.</span></span>|  
|<span data-ttu-id="29762-155">**/Code** *[: dosya]*</span><span class="sxs-lookup"><span data-stu-id="29762-155">**/code** *[:file]*</span></span>|<span data-ttu-id="29762-156">Çıkışı kaynak kodu olarak gönderir.</span><span class="sxs-lookup"><span data-stu-id="29762-156">Sends output as source code.</span></span> <span data-ttu-id="29762-157">**/DBML** seçeneğiyle birlikte kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="29762-157">Cannot be used with **/dbml** option.</span></span>|  
|<span data-ttu-id="29762-158">**/Map** *[: dosya]*</span><span class="sxs-lookup"><span data-stu-id="29762-158">**/map** *[:file]*</span></span>|<span data-ttu-id="29762-159">Öznitelikler yerine bir XML eşleme dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="29762-159">Generates an XML mapping file instead of attributes.</span></span> <span data-ttu-id="29762-160">**/DBML** seçeneğiyle birlikte kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="29762-160">Cannot be used with **/dbml** option.</span></span>|  
  
 <span data-ttu-id="29762-161">**Çeşitli**</span><span class="sxs-lookup"><span data-stu-id="29762-161">**Miscellaneous**</span></span>  
  
|<span data-ttu-id="29762-162">Seçenek</span><span class="sxs-lookup"><span data-stu-id="29762-162">Option</span></span>|<span data-ttu-id="29762-163">Açıklama</span><span class="sxs-lookup"><span data-stu-id="29762-163">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="29762-164">**/Language:**  *dil\<>*</span><span class="sxs-lookup"><span data-stu-id="29762-164">**/language:** *\<language>*</span></span>|<span data-ttu-id="29762-165">Kaynak kod dilini belirtir.</span><span class="sxs-lookup"><span data-stu-id="29762-165">Specifies source code language.</span></span><br /><br /> <span data-ttu-id="29762-166">*Geçerli\<dil >* : vb, CSharp.</span><span class="sxs-lookup"><span data-stu-id="29762-166">Valid *\<language>*: vb, csharp.</span></span><br /><br /> <span data-ttu-id="29762-167">Varsayılan değer: Kod dosyası adındaki uzantıdan türetilir.</span><span class="sxs-lookup"><span data-stu-id="29762-167">Default value: Derived from extension on code file name.</span></span>|  
|<span data-ttu-id="29762-168">**/Namespace:**  *ad\<>*</span><span class="sxs-lookup"><span data-stu-id="29762-168">**/namespace:** *\<name>*</span></span>|<span data-ttu-id="29762-169">Üretilen kodun ad alanını belirtir.</span><span class="sxs-lookup"><span data-stu-id="29762-169">Specifies namespace of the generated code.</span></span> <span data-ttu-id="29762-170">Varsayılan değer: ad alanı yok.</span><span class="sxs-lookup"><span data-stu-id="29762-170">Default value: no namespace.</span></span>|  
|<span data-ttu-id="29762-171">**/Context:**  *tür\<>*</span><span class="sxs-lookup"><span data-stu-id="29762-171">**/context:** *\<type>*</span></span>|<span data-ttu-id="29762-172">Veri bağlamı sınıfının adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="29762-172">Specifies name of data context class.</span></span> <span data-ttu-id="29762-173">Varsayılan değer: Veritabanı adından türetilir.</span><span class="sxs-lookup"><span data-stu-id="29762-173">Default value: Derived from database name.</span></span>|  
|<span data-ttu-id="29762-174">**/entitybase:**  *tür\<>*</span><span class="sxs-lookup"><span data-stu-id="29762-174">**/entitybase:** *\<type>*</span></span>|<span data-ttu-id="29762-175">Üretilen kodda varlık sınıflarının temel sınıfını belirtir.</span><span class="sxs-lookup"><span data-stu-id="29762-175">Specifies the base class of the entity classes in the generated code.</span></span> <span data-ttu-id="29762-176">Varsayılan değer: Varlıkların temel sınıfı yok.</span><span class="sxs-lookup"><span data-stu-id="29762-176">Default value: Entities have no base class.</span></span>|  
|<span data-ttu-id="29762-177">**/plurleştir**</span><span class="sxs-lookup"><span data-stu-id="29762-177">**/pluralize**</span></span>|<span data-ttu-id="29762-178">Sınıf ve üye adlarını otomatik olarak çoğullaştırır veya tekilleştirir.</span><span class="sxs-lookup"><span data-stu-id="29762-178">Automatically pluralizes or singularizes class and member names.</span></span><br /><br /> <span data-ttu-id="29762-179">Bu seçenek yalnızca ABD 'de kullanılabilir İngilizce sürümü.</span><span class="sxs-lookup"><span data-stu-id="29762-179">This option is available only in the U.S. English version.</span></span>|  
|<span data-ttu-id="29762-180">**/Serialization:**  *seçenek\<>*</span><span class="sxs-lookup"><span data-stu-id="29762-180">**/serialization:** *\<option>*</span></span>|<span data-ttu-id="29762-181">Seri hale getirilebilir sınıflar oluşturur.</span><span class="sxs-lookup"><span data-stu-id="29762-181">Generates serializable classes.</span></span><br /><br /> <span data-ttu-id="29762-182">*Geçerli\<Seçenek >* : Hiçbiri, tek yönlü.</span><span class="sxs-lookup"><span data-stu-id="29762-182">Valid *\<option>*: None, Unidirectional.</span></span> <span data-ttu-id="29762-183">Varsayılan değer: Yok.</span><span class="sxs-lookup"><span data-stu-id="29762-183">Default value: None.</span></span><br /><br /> <span data-ttu-id="29762-184">Daha fazla bilgi için bkz. [serileştirme](../../../docs/framework/data/adonet/sql/linq/serialization.md).</span><span class="sxs-lookup"><span data-stu-id="29762-184">For more information, see [Serialization](../../../docs/framework/data/adonet/sql/linq/serialization.md).</span></span>|  
  
 <span data-ttu-id="29762-185">**Giriş dosyası**</span><span class="sxs-lookup"><span data-stu-id="29762-185">**Input File**</span></span>  
  
|<span data-ttu-id="29762-186">Seçenek</span><span class="sxs-lookup"><span data-stu-id="29762-186">Option</span></span>|<span data-ttu-id="29762-187">Açıklama</span><span class="sxs-lookup"><span data-stu-id="29762-187">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="29762-188">**\<giriş dosyası >**</span><span class="sxs-lookup"><span data-stu-id="29762-188">**\<input file>**</span></span>|<span data-ttu-id="29762-189">Bir SQL Server Express. mdf dosyası, bir SQL Server Compact 3,5. sdf dosyası veya. dbml ara dosyası belirtir.</span><span class="sxs-lookup"><span data-stu-id="29762-189">Specifies a SQL Server Express .mdf file, a SQL Server Compact 3.5 .sdf file, or a .dbml intermediate file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="29762-190">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="29762-190">Remarks</span></span>  
 <span data-ttu-id="29762-191">SqlMetal işlevi aslında iki adımdan oluşur:</span><span class="sxs-lookup"><span data-stu-id="29762-191">SqlMetal functionality actually involves two steps:</span></span>  
  
- <span data-ttu-id="29762-192">Veritabanını meta verilerini bir .dbml dosyasına ayıklama.</span><span class="sxs-lookup"><span data-stu-id="29762-192">Extracting the metadata of the database into a .dbml file.</span></span>  
  
- <span data-ttu-id="29762-193">Kod çıktı dosyası oluşturma.</span><span class="sxs-lookup"><span data-stu-id="29762-193">Generating a code output file.</span></span>  
  
     <span data-ttu-id="29762-194">Uygun komut satırı seçeneklerini kullanarak Visual Basic veya C# kaynak kodu oluşturabilir veya bir XML eşleme dosyası üretebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="29762-194">By using the appropriate command-line options, you can produce Visual Basic or C# source code, or you can produce an XML mapping file.</span></span>  
  
 <span data-ttu-id="29762-195">Meta verileri bir .mdf dosyasından ayıklamak için, .mdf dosyası adını tüm diğer seçeneklerden sonra belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="29762-195">To extract the metadata from an .mdf file, you must specify the name of the .mdf file after all other options.</span></span>  
  
 <span data-ttu-id="29762-196">**/Server** belirtilmemişse, **localhost/sqlexpress** varsayılır.</span><span class="sxs-lookup"><span data-stu-id="29762-196">If no **/server** is specified, **localhost/sqlexpress** is assumed.</span></span>  
  
 <span data-ttu-id="29762-197">Microsoft SQL Server 2005 aşağıdaki koşullardan biri veya daha fazlası doğru ise bir özel durum oluşturur:</span><span class="sxs-lookup"><span data-stu-id="29762-197">Microsoft SQL Server 2005 throws an exception if one or more of the following conditions are true:</span></span>  
  
- <span data-ttu-id="29762-198">SqlMetal, kendi kendini çağıran bir saklı yordam ayıklamaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="29762-198">SqlMetal tries to extract a stored procedure that calls itself.</span></span>  
  
- <span data-ttu-id="29762-199">Bir saklı yordam, işlev veya görünümün iç içe geçme düzeyini 32'yi aşıyor.</span><span class="sxs-lookup"><span data-stu-id="29762-199">The nesting level of a stored procedure, function, or view exceeds 32.</span></span>  
  
     <span data-ttu-id="29762-200">SqlMetal, bu özel durumu yakalar ve bir uyarı olarak bildirir.</span><span class="sxs-lookup"><span data-stu-id="29762-200">SqlMetal catches this exception and reports it as a warning.</span></span>  
  
 <span data-ttu-id="29762-201">Bir giriş dosyası adı belirtmek için, adı komut satırına giriş dosyası olarak ekleyin.</span><span class="sxs-lookup"><span data-stu-id="29762-201">To specify an input file name, add the name to the command line as the input file.</span></span> <span data-ttu-id="29762-202">Dosya adının bağlantı dizesine dahil edilmesi ( **/Conn** seçeneği kullanılarak) desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="29762-202">Including the file name in the connection string (using the **/conn** option) is not supported.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="29762-203">Örnekler</span><span class="sxs-lookup"><span data-stu-id="29762-203">Examples</span></span>  
 <span data-ttu-id="29762-204">Ayıklanan SQL meta verileri içeren bir .dbml dosyası oluşturun:</span><span class="sxs-lookup"><span data-stu-id="29762-204">Generate a .dbml file that includes extracted SQL metadata:</span></span>  
  
 <span data-ttu-id="29762-205">**SqlMetal/Server: sunucum/veritabanı: Northwind/DBML: mymeta. dbml**</span><span class="sxs-lookup"><span data-stu-id="29762-205">**sqlmetal /server:myserver /database:northwind /dbml:mymeta.dbml**</span></span>  
  
 <span data-ttu-id="29762-206">SQL Server Express kullanarak bir .mdf dosyasından ayıklanan SQL meta verilerini içeren bir .dbml dosyası oluşturun:</span><span class="sxs-lookup"><span data-stu-id="29762-206">Generate a .dbml file that includes extracted SQL metadata from an .mdf file by using SQL Server Express:</span></span>  
  
 <span data-ttu-id="29762-207">**SqlMetal/DBML: mymeta. dbml mydbfile. mdf**</span><span class="sxs-lookup"><span data-stu-id="29762-207">**sqlmetal /dbml:mymeta.dbml mydbfile.mdf**</span></span>  
  
 <span data-ttu-id="29762-208">SQL Server Express'ten ayıklanan SQL meta verilerini içeren bir .dbml dosyası oluşturun:</span><span class="sxs-lookup"><span data-stu-id="29762-208">Generate a .dbml file that includes extracted SQL metadata from SQL Server Express:</span></span>  
  
 <span data-ttu-id="29762-209">**sqlmetal /server:.\sqlexpress /dbml:mymeta.dbml /database:northwind**</span><span class="sxs-lookup"><span data-stu-id="29762-209">**sqlmetal /server:.\sqlexpress /dbml:mymeta.dbml /database:northwind**</span></span>  
  
 <span data-ttu-id="29762-210">Dbml meta veri dosyasından kaynak kodu oluşturun:</span><span class="sxs-lookup"><span data-stu-id="29762-210">Generate source code from a .dbml metadata file:</span></span>  
  
 <span data-ttu-id="29762-211">**SqlMetal/Namespace: Nwind/Code: nrüzgar. cs/Language: CSharp mymetal. dbml**</span><span class="sxs-lookup"><span data-stu-id="29762-211">**sqlmetal /namespace:nwind /code:nwind.cs /language:csharp mymetal.dbml**</span></span>  
  
 <span data-ttu-id="29762-212">Doğrudan SQL meta verilerinden kaynak kodu oluşturun:</span><span class="sxs-lookup"><span data-stu-id="29762-212">Generate source code from SQL metadata directly:</span></span>  
  
 <span data-ttu-id="29762-213">**SqlMetal/Server: sunucum/veritabanı: Northwind/Namespace: Nwind/Code: nrüzgar. cs/Language: CSharp**</span><span class="sxs-lookup"><span data-stu-id="29762-213">**sqlmetal /server:myserver /database:northwind /namespace:nwind /code:nwind.cs /language:csharp**</span></span>  
  
> [!NOTE]
> <span data-ttu-id="29762-214">Northwind örnek veritabanıyla **/plurleştir** seçeneğini kullandığınızda aşağıdaki davranışa göz önünde bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="29762-214">When you use the **/pluralize** option with the Northwind sample database, note the following behavior.</span></span> <span data-ttu-id="29762-215">SqlMetal tablolar için satır türünde adlar oluşturduğunda, tablo adları tekildir.</span><span class="sxs-lookup"><span data-stu-id="29762-215">When SqlMetal makes row-type names for tables, the table names are singular.</span></span> <span data-ttu-id="29762-216">Tablolar için Özellikler <xref:System.Data.Linq.DataContext> yaptığında tablo adları plural olur.</span><span class="sxs-lookup"><span data-stu-id="29762-216">When it makes <xref:System.Data.Linq.DataContext> properties for tables, the table names are plural.</span></span> <span data-ttu-id="29762-217">Tesadüfen, Northwind örnek veritabanındaki tablolar zaten çoğuldur.</span><span class="sxs-lookup"><span data-stu-id="29762-217">Coincidentally, the tables in the Northwind sample database are already plural.</span></span> <span data-ttu-id="29762-218">Bu nedenle, bu bölümün çalıştığını görmezsiniz.</span><span class="sxs-lookup"><span data-stu-id="29762-218">Therefore, you do not see that part working.</span></span> <span data-ttu-id="29762-219">Veritabanı tablolarını tekil olarak adlandırmak ortak uygulama olsa da, toplulukları çoğul olarak adlandırmak da .NET'te ortak bir uygulamadır.</span><span class="sxs-lookup"><span data-stu-id="29762-219">Although it is common practice to name database tables singular, it is also a common practice in .NET to name collections plural.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29762-220">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="29762-220">See also</span></span>

- [<span data-ttu-id="29762-221">Nasıl yapılır: Visual Basic veya içinde nesne modeli oluşturmaC#</span><span class="sxs-lookup"><span data-stu-id="29762-221">How to: Generate the Object Model in Visual Basic or C#</span></span>](../../../docs/framework/data/adonet/sql/linq/how-to-generate-the-object-model-in-visual-basic-or-csharp.md)
- [<span data-ttu-id="29762-222">LINQ to SQL’de Kod Oluşturma</span><span class="sxs-lookup"><span data-stu-id="29762-222">Code Generation in LINQ to SQL</span></span>](../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)
- [<span data-ttu-id="29762-223">Dış Eşleme</span><span class="sxs-lookup"><span data-stu-id="29762-223">External Mapping</span></span>](../../../docs/framework/data/adonet/sql/linq/external-mapping.md)
