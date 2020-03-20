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
ms.openlocfilehash: d5b4c2b59b585b3d3a3584ef9055e70c9d998e85
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "71044085"
---
# <a name="sqlmetalexe-code-generation-tool"></a><span data-ttu-id="38da6-102">SqlMetal.exe (Kod Üretme Aracı)</span><span class="sxs-lookup"><span data-stu-id="38da6-102">SqlMetal.exe (Code Generation Tool)</span></span>
<span data-ttu-id="38da6-103">SqlMetal komut satırı aracı,.NET Framework [!INCLUDE[vbtecdlinq](../../../includes/vbtecdlinq-md.md)] bileşeni için kod ve eşleme oluşturur.</span><span class="sxs-lookup"><span data-stu-id="38da6-103">The SqlMetal command-line tool generates code and mapping for the [!INCLUDE[vbtecdlinq](../../../includes/vbtecdlinq-md.md)] component of the .NET Framework.</span></span> <span data-ttu-id="38da6-104">Bu konunun ilerisinde görünen seçenekleri uygulayarak, SqlMetal'den aşağıdakileri içeren çeşitli farklı eylemler gerçekleştirmesini isteyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="38da6-104">By applying options that appear later in this topic, you can instruct SqlMetal to perform several different actions that include the following:</span></span>  
  
- <span data-ttu-id="38da6-105">Bir veritabanından, kaynak kodu ve eşleme öznitelikleri veya bir eşleme dosyası oluşturmak.</span><span class="sxs-lookup"><span data-stu-id="38da6-105">From a database, generate source code and mapping attributes or a mapping file.</span></span>  
  
- <span data-ttu-id="38da6-106">Bir veritabanından, dosya özelleştirme için bir ara veritabanı işaretleme dili (.dbml) dosyası oluşturmak.</span><span class="sxs-lookup"><span data-stu-id="38da6-106">From a database, generate an intermediate database markup language (.dbml) file for customization.</span></span>  
  
- <span data-ttu-id="38da6-107">Bir .dbml dosyasından, kod veya eşleme öznitelikleri veya bir eşleme dosyası üretmek.</span><span class="sxs-lookup"><span data-stu-id="38da6-107">From a .dbml file, generate code and mapping attributes or a mapping file.</span></span>  
  
 <span data-ttu-id="38da6-108">Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir.</span><span class="sxs-lookup"><span data-stu-id="38da6-108">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="38da6-109">Varsayılan olarak, dosya :\Program Files\Microsoft `drive`SDKs\Windows\v`n.nn`\bin adresinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="38da6-109">By default, the file is located at `drive`:\Program Files\Microsoft SDKs\Windows\v`n.nn`\bin.</span></span> <span data-ttu-id="38da6-110">Visual Studio'yu yüklemezseniz, [Windows SDK'yı](https://go.microsoft.com/fwlink/?LinkId=142225)indirerek SQLMetal dosyasını da alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="38da6-110">If you do not install Visual Studio, you can also get the SQLMetal file by downloading the [Windows SDK](https://go.microsoft.com/fwlink/?LinkId=142225).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="38da6-111">Visual Studio kullanan geliştiriciler, varlık sınıfları oluşturmak için Object İlişkisel Tasarımcı'yı da kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="38da6-111">Developers who use Visual Studio can also use the Object Relational Designer to generate entity classes.</span></span> <span data-ttu-id="38da6-112">Komut satırı yaklaşımı, büyük veritabanları için uygun düşmektedir.</span><span class="sxs-lookup"><span data-stu-id="38da6-112">The command-line approach scales well for large databases.</span></span> <span data-ttu-id="38da6-113">SqlMetal bir komut satırı aracı olduğundan, bir oluşturma işleminde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="38da6-113">Because SqlMetal is a command-line tool, you can use it in a build process.</span></span>  
  
 <span data-ttu-id="38da6-114">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span><span class="sxs-lookup"><span data-stu-id="38da6-114">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="38da6-115">Daha fazla bilgi için [Komut İstemleri'ne](developer-command-prompt-for-vs.md)bakın. Komut isteminde aşağıdakileri yazın:</span><span class="sxs-lookup"><span data-stu-id="38da6-115">For more information, see [Command Prompts](developer-command-prompt-for-vs.md).At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38da6-116">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="38da6-116">Syntax</span></span>  
  
```console  
sqlmetal [options] [<input file>]  
```  
  
## <a name="options"></a><span data-ttu-id="38da6-117">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="38da6-117">Options</span></span>  
 <span data-ttu-id="38da6-118">En güncel seçenek listesini görüntülemek `sqlmetal /?` için, yüklenen konumdan komut istemine yazın.</span><span class="sxs-lookup"><span data-stu-id="38da6-118">To view the most current option list, type `sqlmetal /?` at a command prompt from the installed location.</span></span>  
  
 <span data-ttu-id="38da6-119">**Bağlantı Seçenekleri**</span><span class="sxs-lookup"><span data-stu-id="38da6-119">**Connection Options**</span></span>  
  
|<span data-ttu-id="38da6-120">Seçenek</span><span class="sxs-lookup"><span data-stu-id="38da6-120">Option</span></span>|<span data-ttu-id="38da6-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="38da6-121">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="38da6-122">**/server:** \* \<isim>\*</span><span class="sxs-lookup"><span data-stu-id="38da6-122">**/server:** *\<name>*</span></span>|<span data-ttu-id="38da6-123">Veritabanı sunucusu adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="38da6-123">Specifies database server name.</span></span>|  
|<span data-ttu-id="38da6-124">**/database:** \* \<isim>\*</span><span class="sxs-lookup"><span data-stu-id="38da6-124">**/database:** *\<name>*</span></span>|<span data-ttu-id="38da6-125">Sunucuda veritabanı kataloğu belirtir.</span><span class="sxs-lookup"><span data-stu-id="38da6-125">Specifies database catalog on server.</span></span>|  
|<span data-ttu-id="38da6-126">**/kullanıcı:** \* \<isim>\*</span><span class="sxs-lookup"><span data-stu-id="38da6-126">**/user:** *\<name>*</span></span>|<span data-ttu-id="38da6-127">Oturum açma kullanıcı kimliğini belirtir. Varsayılan değer: Windows kimlik doğrulamasını kullanın.</span><span class="sxs-lookup"><span data-stu-id="38da6-127">Specifies logon user id. Default value: Use Windows authentication.</span></span>|  
|<span data-ttu-id="38da6-128">**/password:** \* \<şifre>\*</span><span class="sxs-lookup"><span data-stu-id="38da6-128">**/password:** *\<password>*</span></span>|<span data-ttu-id="38da6-129">Oturum açma parolasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="38da6-129">Specifies logon password.</span></span> <span data-ttu-id="38da6-130">Varsayılan değer: Windows kimlik doğrulaması kullan.</span><span class="sxs-lookup"><span data-stu-id="38da6-130">Default value: Use Windows authentication.</span></span>|  
|<span data-ttu-id="38da6-131">**/conn:** \* \<bağlantı dizesi>\*</span><span class="sxs-lookup"><span data-stu-id="38da6-131">**/conn:** *\<connection string>*</span></span>|<span data-ttu-id="38da6-132">Veritabanı bağlantısı dizesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="38da6-132">Specifies database connection string.</span></span> <span data-ttu-id="38da6-133">**/server**, /database , **/user**, veya **/password** seçenekleri yle kullanılamaz. **/database**</span><span class="sxs-lookup"><span data-stu-id="38da6-133">Cannot be used with **/server**, **/database**, **/user**, or **/password** options.</span></span><br /><br /> <span data-ttu-id="38da6-134">Dosya adını bağlantı dizesine eklemeyin.</span><span class="sxs-lookup"><span data-stu-id="38da6-134">Do not include the file name in the connection string.</span></span> <span data-ttu-id="38da6-135">Bunun yerine, dosya adını giriş dosyası olarak komut satırına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="38da6-135">Instead, add the file name to the command line as the input file.</span></span> <span data-ttu-id="38da6-136">Örneğin, aşağıdaki satırda "c:\northwnd.mdf" giriş dosyası olarak belirtilir: **sqlmetal /code:"c:\northwind.cs" /language:csharp "c:\northwnd.mdf"**.</span><span class="sxs-lookup"><span data-stu-id="38da6-136">For example, the following line specifies "c:\northwnd.mdf" as the input file: **sqlmetal /code:"c:\northwind.cs" /language:csharp "c:\northwnd.mdf"**.</span></span>|  
|<span data-ttu-id="38da6-137">**/timetime:** \* \<saniye>\*</span><span class="sxs-lookup"><span data-stu-id="38da6-137">**/timeout:** *\<seconds>*</span></span>|<span data-ttu-id="38da6-138">SqlMetal veritabanına eriştiğinde, zaman aşımı değerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="38da6-138">Specifies time-out value when SqlMetal accesses the database.</span></span> <span data-ttu-id="38da6-139">Varsayılan değer: 0 (yani, zaman sınırı yok).</span><span class="sxs-lookup"><span data-stu-id="38da6-139">Default value: 0 (that is, no time limit).</span></span>|  
  
 <span data-ttu-id="38da6-140">**Çıkarma seçenekleri**</span><span class="sxs-lookup"><span data-stu-id="38da6-140">**Extraction options**</span></span>  
  
|<span data-ttu-id="38da6-141">Seçenek</span><span class="sxs-lookup"><span data-stu-id="38da6-141">Option</span></span>|<span data-ttu-id="38da6-142">Açıklama</span><span class="sxs-lookup"><span data-stu-id="38da6-142">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="38da6-143">**/görünümler**</span><span class="sxs-lookup"><span data-stu-id="38da6-143">**/views**</span></span>|<span data-ttu-id="38da6-144">Veritabanı görünümlerini ayıklar.</span><span class="sxs-lookup"><span data-stu-id="38da6-144">Extracts database views.</span></span>|  
|<span data-ttu-id="38da6-145">**/fonksiyonlar**</span><span class="sxs-lookup"><span data-stu-id="38da6-145">**/functions**</span></span>|<span data-ttu-id="38da6-146">Veritabanı işlevlerini ayıklar.</span><span class="sxs-lookup"><span data-stu-id="38da6-146">Extracts database functions.</span></span>|  
|<span data-ttu-id="38da6-147">**/sprocs**</span><span class="sxs-lookup"><span data-stu-id="38da6-147">**/sprocs**</span></span>|<span data-ttu-id="38da6-148">Saklı yordamları ayıklar.</span><span class="sxs-lookup"><span data-stu-id="38da6-148">Extracts stored procedures.</span></span>|  
  
 <span data-ttu-id="38da6-149">**Çıkış seçenekleri**</span><span class="sxs-lookup"><span data-stu-id="38da6-149">**Output options**</span></span>  
  
|<span data-ttu-id="38da6-150">Seçenek</span><span class="sxs-lookup"><span data-stu-id="38da6-150">Option</span></span>|<span data-ttu-id="38da6-151">Açıklama</span><span class="sxs-lookup"><span data-stu-id="38da6-151">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="38da6-152">**/dbml** *[:dosya]*</span><span class="sxs-lookup"><span data-stu-id="38da6-152">**/dbml** *[:file]*</span></span>|<span data-ttu-id="38da6-153">Çıkışı .dbml olarak gönderir.</span><span class="sxs-lookup"><span data-stu-id="38da6-153">Sends output as .dbml.</span></span> <span data-ttu-id="38da6-154">**/harita** seçeneği ile kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="38da6-154">Cannot be used with **/map** option.</span></span>|  
|<span data-ttu-id="38da6-155">**/kod** *[:dosya]*</span><span class="sxs-lookup"><span data-stu-id="38da6-155">**/code** *[:file]*</span></span>|<span data-ttu-id="38da6-156">Çıkışı kaynak kodu olarak gönderir.</span><span class="sxs-lookup"><span data-stu-id="38da6-156">Sends output as source code.</span></span> <span data-ttu-id="38da6-157">**/dbml** seçeneği ile kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="38da6-157">Cannot be used with **/dbml** option.</span></span>|  
|<span data-ttu-id="38da6-158">**/harita** *[:dosya]*</span><span class="sxs-lookup"><span data-stu-id="38da6-158">**/map** *[:file]*</span></span>|<span data-ttu-id="38da6-159">Öznitelikler yerine bir XML eşleme dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="38da6-159">Generates an XML mapping file instead of attributes.</span></span> <span data-ttu-id="38da6-160">**/dbml** seçeneği ile kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="38da6-160">Cannot be used with **/dbml** option.</span></span>|  
  
 <span data-ttu-id="38da6-161">**Çeşitli**</span><span class="sxs-lookup"><span data-stu-id="38da6-161">**Miscellaneous**</span></span>  
  
|<span data-ttu-id="38da6-162">Seçenek</span><span class="sxs-lookup"><span data-stu-id="38da6-162">Option</span></span>|<span data-ttu-id="38da6-163">Açıklama</span><span class="sxs-lookup"><span data-stu-id="38da6-163">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="38da6-164">**/language:** \* \<dil>\*</span><span class="sxs-lookup"><span data-stu-id="38da6-164">**/language:** *\<language>*</span></span>|<span data-ttu-id="38da6-165">Kaynak kod dilini belirtir.</span><span class="sxs-lookup"><span data-stu-id="38da6-165">Specifies source code language.</span></span><br /><br /> <span data-ttu-id="38da6-166">Geçerli \* \<dil>\*: vb, csharp.</span><span class="sxs-lookup"><span data-stu-id="38da6-166">Valid *\<language>*: vb, csharp.</span></span><br /><br /> <span data-ttu-id="38da6-167">Varsayılan değer: Kod dosyası adındaki uzantıdan türetilir.</span><span class="sxs-lookup"><span data-stu-id="38da6-167">Default value: Derived from extension on code file name.</span></span>|  
|<span data-ttu-id="38da6-168">**/namespace:** \* \<isim>\*</span><span class="sxs-lookup"><span data-stu-id="38da6-168">**/namespace:** *\<name>*</span></span>|<span data-ttu-id="38da6-169">Üretilen kodun ad alanını belirtir.</span><span class="sxs-lookup"><span data-stu-id="38da6-169">Specifies namespace of the generated code.</span></span> <span data-ttu-id="38da6-170">Varsayılan değer: ad alanı yok.</span><span class="sxs-lookup"><span data-stu-id="38da6-170">Default value: no namespace.</span></span>|  
|<span data-ttu-id="38da6-171">**/context:** \* \<tip>\*</span><span class="sxs-lookup"><span data-stu-id="38da6-171">**/context:** *\<type>*</span></span>|<span data-ttu-id="38da6-172">Veri bağlamı sınıfının adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="38da6-172">Specifies name of data context class.</span></span> <span data-ttu-id="38da6-173">Varsayılan değer: Veritabanı adından türetilir.</span><span class="sxs-lookup"><span data-stu-id="38da6-173">Default value: Derived from database name.</span></span>|  
|<span data-ttu-id="38da6-174">**/entitybase:** \* \<tip>\*</span><span class="sxs-lookup"><span data-stu-id="38da6-174">**/entitybase:** *\<type>*</span></span>|<span data-ttu-id="38da6-175">Üretilen kodda varlık sınıflarının temel sınıfını belirtir.</span><span class="sxs-lookup"><span data-stu-id="38da6-175">Specifies the base class of the entity classes in the generated code.</span></span> <span data-ttu-id="38da6-176">Varsayılan değer: Varlıkların temel sınıfı yoktur.</span><span class="sxs-lookup"><span data-stu-id="38da6-176">Default value: Entities have no base class.</span></span>|  
|<span data-ttu-id="38da6-177">**/çoğulize**</span><span class="sxs-lookup"><span data-stu-id="38da6-177">**/pluralize**</span></span>|<span data-ttu-id="38da6-178">Sınıf ve üye adlarını otomatik olarak çoğullaştırır veya tekilleştirir.</span><span class="sxs-lookup"><span data-stu-id="38da6-178">Automatically pluralizes or singularizes class and member names.</span></span><br /><br /> <span data-ttu-id="38da6-179">Bu seçenek yalnızca ABD İngilizcesi sürümünde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="38da6-179">This option is available only in the U.S. English version.</span></span>|  
|<span data-ttu-id="38da6-180">**/serialization:** \* \<seçenek>\*</span><span class="sxs-lookup"><span data-stu-id="38da6-180">**/serialization:** *\<option>*</span></span>|<span data-ttu-id="38da6-181">Seri hale getirilebilir sınıflar oluşturur.</span><span class="sxs-lookup"><span data-stu-id="38da6-181">Generates serializable classes.</span></span><br /><br /> <span data-ttu-id="38da6-182">Geçerli \* \<seçenek>\*: Yok, Tek yönlü.</span><span class="sxs-lookup"><span data-stu-id="38da6-182">Valid *\<option>*: None, Unidirectional.</span></span> <span data-ttu-id="38da6-183">Varsayılan değer: Hiçbiri.</span><span class="sxs-lookup"><span data-stu-id="38da6-183">Default value: None.</span></span><br /><br /> <span data-ttu-id="38da6-184">Daha fazla bilgi için [Serileştirme'ye](../data/adonet/sql/linq/serialization.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="38da6-184">For more information, see [Serialization](../data/adonet/sql/linq/serialization.md).</span></span>|  
  
 <span data-ttu-id="38da6-185">**Giriş Dosyası**</span><span class="sxs-lookup"><span data-stu-id="38da6-185">**Input File**</span></span>  
  
|<span data-ttu-id="38da6-186">Seçenek</span><span class="sxs-lookup"><span data-stu-id="38da6-186">Option</span></span>|<span data-ttu-id="38da6-187">Açıklama</span><span class="sxs-lookup"><span data-stu-id="38da6-187">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="38da6-188">**\<giriş dosyası>**</span><span class="sxs-lookup"><span data-stu-id="38da6-188">**\<input file>**</span></span>|<span data-ttu-id="38da6-189">SQL Server Express .mdf dosyası, SQL Server Compact 3.5 .sdf dosyası veya .dbml ara dosya belirtir.</span><span class="sxs-lookup"><span data-stu-id="38da6-189">Specifies a SQL Server Express .mdf file, a SQL Server Compact 3.5 .sdf file, or a .dbml intermediate file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="38da6-190">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="38da6-190">Remarks</span></span>  
 <span data-ttu-id="38da6-191">SqlMetal işlevi aslında iki adımdan oluşur:</span><span class="sxs-lookup"><span data-stu-id="38da6-191">SqlMetal functionality actually involves two steps:</span></span>  
  
- <span data-ttu-id="38da6-192">Veritabanını meta verilerini bir .dbml dosyasına ayıklama.</span><span class="sxs-lookup"><span data-stu-id="38da6-192">Extracting the metadata of the database into a .dbml file.</span></span>  
  
- <span data-ttu-id="38da6-193">Kod çıktı dosyası oluşturma.</span><span class="sxs-lookup"><span data-stu-id="38da6-193">Generating a code output file.</span></span>  
  
     <span data-ttu-id="38da6-194">Uygun komut satırı seçeneklerini kullanarak Visual Basic veya C# kaynak kodu üretebilir veya bir XML eşleme dosyası oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="38da6-194">By using the appropriate command-line options, you can produce Visual Basic or C# source code, or you can produce an XML mapping file.</span></span>  
  
 <span data-ttu-id="38da6-195">Meta verileri bir .mdf dosyasından ayıklamak için, .mdf dosyası adını tüm diğer seçeneklerden sonra belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="38da6-195">To extract the metadata from an .mdf file, you must specify the name of the .mdf file after all other options.</span></span>  
  
 <span data-ttu-id="38da6-196">**/sunucu belirtilmemişse,** **localhost/sqlexpress** varsayılr.</span><span class="sxs-lookup"><span data-stu-id="38da6-196">If no **/server** is specified, **localhost/sqlexpress** is assumed.</span></span>  
  
 <span data-ttu-id="38da6-197">Microsoft SQL Server 2005, aşağıdaki koşullardan biri veya birkaçı doğruysa bir özel durum oluşturur:</span><span class="sxs-lookup"><span data-stu-id="38da6-197">Microsoft SQL Server 2005 throws an exception if one or more of the following conditions are true:</span></span>  
  
- <span data-ttu-id="38da6-198">SqlMetal, kendi kendini çağıran bir saklı yordam ayıklamaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="38da6-198">SqlMetal tries to extract a stored procedure that calls itself.</span></span>  
  
- <span data-ttu-id="38da6-199">Bir saklı yordam, işlev veya görünümün iç içe geçme düzeyini 32'yi aşıyor.</span><span class="sxs-lookup"><span data-stu-id="38da6-199">The nesting level of a stored procedure, function, or view exceeds 32.</span></span>  
  
     <span data-ttu-id="38da6-200">SqlMetal, bu özel durumu yakalar ve bir uyarı olarak bildirir.</span><span class="sxs-lookup"><span data-stu-id="38da6-200">SqlMetal catches this exception and reports it as a warning.</span></span>  
  
 <span data-ttu-id="38da6-201">Bir giriş dosyası adı belirtmek için, adı komut satırına giriş dosyası olarak ekleyin.</span><span class="sxs-lookup"><span data-stu-id="38da6-201">To specify an input file name, add the name to the command line as the input file.</span></span> <span data-ttu-id="38da6-202">Bağlantı dizesindeki dosya adının eklenmesi **(/conn** seçeneğini kullanarak) desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="38da6-202">Including the file name in the connection string (using the **/conn** option) is not supported.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="38da6-203">Örnekler</span><span class="sxs-lookup"><span data-stu-id="38da6-203">Examples</span></span>  
 <span data-ttu-id="38da6-204">Ayıklanan SQL meta verileri içeren bir .dbml dosyası oluşturun:</span><span class="sxs-lookup"><span data-stu-id="38da6-204">Generate a .dbml file that includes extracted SQL metadata:</span></span>  
  
 <span data-ttu-id="38da6-205">**sqlmetal /server:myserver /database:northwind /dbml:mymeta.dbml**</span><span class="sxs-lookup"><span data-stu-id="38da6-205">**sqlmetal /server:myserver /database:northwind /dbml:mymeta.dbml**</span></span>  
  
 <span data-ttu-id="38da6-206">SQL Server Express kullanarak bir .mdf dosyasından ayıklanan SQL meta verilerini içeren bir .dbml dosyası oluşturun:</span><span class="sxs-lookup"><span data-stu-id="38da6-206">Generate a .dbml file that includes extracted SQL metadata from an .mdf file by using SQL Server Express:</span></span>  
  
 <span data-ttu-id="38da6-207">**sqlmetal /dbml:mymeta.dbml mydbfile.mdf**</span><span class="sxs-lookup"><span data-stu-id="38da6-207">**sqlmetal /dbml:mymeta.dbml mydbfile.mdf**</span></span>  
  
 <span data-ttu-id="38da6-208">SQL Server Express'ten ayıklanan SQL meta verilerini içeren bir .dbml dosyası oluşturun:</span><span class="sxs-lookup"><span data-stu-id="38da6-208">Generate a .dbml file that includes extracted SQL metadata from SQL Server Express:</span></span>  
  
 <span data-ttu-id="38da6-209">**sqlmetal /server:.\sqlexpress /dbml:mymeta.dbml /database:northwind**</span><span class="sxs-lookup"><span data-stu-id="38da6-209">**sqlmetal /server:.\sqlexpress /dbml:mymeta.dbml /database:northwind**</span></span>  
  
 <span data-ttu-id="38da6-210">Dbml meta veri dosyasından kaynak kodu oluşturun:</span><span class="sxs-lookup"><span data-stu-id="38da6-210">Generate source code from a .dbml metadata file:</span></span>  
  
 <span data-ttu-id="38da6-211">**sqlmetal /namespace:nwind /code:nwind.cs /language:csharp mymetal.dbml**</span><span class="sxs-lookup"><span data-stu-id="38da6-211">**sqlmetal /namespace:nwind /code:nwind.cs /language:csharp mymetal.dbml**</span></span>  
  
 <span data-ttu-id="38da6-212">Doğrudan SQL meta verilerinden kaynak kodu oluşturun:</span><span class="sxs-lookup"><span data-stu-id="38da6-212">Generate source code from SQL metadata directly:</span></span>  
  
 <span data-ttu-id="38da6-213">**sqlmetal /server:myserver /database:northwind /namespace:nwind /code:nwind.cs /language:csharp**</span><span class="sxs-lookup"><span data-stu-id="38da6-213">**sqlmetal /server:myserver /database:northwind /namespace:nwind /code:nwind.cs /language:csharp**</span></span>  
  
> [!NOTE]
> <span data-ttu-id="38da6-214">Northwind örnek veritabanıile **/çoğulize** seçeneğini kullandığınızda, aşağıdaki davranışa dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="38da6-214">When you use the **/pluralize** option with the Northwind sample database, note the following behavior.</span></span> <span data-ttu-id="38da6-215">SqlMetal tablolar için satır türünde adlar oluşturduğunda, tablo adları tekildir.</span><span class="sxs-lookup"><span data-stu-id="38da6-215">When SqlMetal makes row-type names for tables, the table names are singular.</span></span> <span data-ttu-id="38da6-216">Tablolar için <xref:System.Data.Linq.DataContext> özellikler yaptığında, tablo adları çoğul olur.</span><span class="sxs-lookup"><span data-stu-id="38da6-216">When it makes <xref:System.Data.Linq.DataContext> properties for tables, the table names are plural.</span></span> <span data-ttu-id="38da6-217">Tesadüfen, Northwind örnek veritabanındaki tablolar zaten çoğuldur.</span><span class="sxs-lookup"><span data-stu-id="38da6-217">Coincidentally, the tables in the Northwind sample database are already plural.</span></span> <span data-ttu-id="38da6-218">Bu nedenle, bu bölümün çalıştığını görmezsiniz.</span><span class="sxs-lookup"><span data-stu-id="38da6-218">Therefore, you do not see that part working.</span></span> <span data-ttu-id="38da6-219">Veritabanı tablolarını tekil olarak adlandırmak ortak uygulama olsa da, toplulukları çoğul olarak adlandırmak da .NET'te ortak bir uygulamadır.</span><span class="sxs-lookup"><span data-stu-id="38da6-219">Although it is common practice to name database tables singular, it is also a common practice in .NET to name collections plural.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38da6-220">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="38da6-220">See also</span></span>

- [<span data-ttu-id="38da6-221">Nasıl yapılır: Visual Basic veya C# içinde Nesne Modeli Oluşturma</span><span class="sxs-lookup"><span data-stu-id="38da6-221">How to: Generate the Object Model in Visual Basic or C#</span></span>](../data/adonet/sql/linq/how-to-generate-the-object-model-in-visual-basic-or-csharp.md)
- [<span data-ttu-id="38da6-222">LINQ to SQL’de Kod Oluşturma</span><span class="sxs-lookup"><span data-stu-id="38da6-222">Code Generation in LINQ to SQL</span></span>](../data/adonet/sql/linq/code-generation-in-linq-to-sql.md)
- [<span data-ttu-id="38da6-223">Dış Eşleme</span><span class="sxs-lookup"><span data-stu-id="38da6-223">External Mapping</span></span>](../data/adonet/sql/linq/external-mapping.md)
