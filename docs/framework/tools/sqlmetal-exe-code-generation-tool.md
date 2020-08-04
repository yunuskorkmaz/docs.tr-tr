---
title: SqlMetal.exe (Kod Üretme Aracı)
description: Kod oluşturma aracını SqlMetal.exe anlayın. .NET ' in LINQ to SQL bileşeni için kod ve eşleme oluşturmak için aracını kullanın.
ms.date: 03/30/2017
helpviewer_keywords:
- SQLMetal [LINQ to SQL]
- code generation tool
- SQLMetal.exe
- LINQ to SQL, serialization
- LINQ to SQL, DBML files
- LINQ to SQL, SQLMetal
ms.assetid: 819e5a96-7646-4fdb-b14b-fe31221b0614
ms.openlocfilehash: 84cad85a7a9fc4b420b57543b7f258607be4ab52
ms.sourcegitcommit: b4f8849c47c1a7145eb26ce68bc9f9976e0dbec3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/03/2020
ms.locfileid: "87517054"
---
# <a name="sqlmetalexe-code-generation-tool"></a><span data-ttu-id="695e8-104">SqlMetal.exe (Kod Üretme Aracı)</span><span class="sxs-lookup"><span data-stu-id="695e8-104">SqlMetal.exe (Code Generation Tool)</span></span>
<span data-ttu-id="695e8-105">SqlMetal komut satırı aracı .NET Framework bileşeni için kod ve eşleme oluşturur [!INCLUDE[vbtecdlinq](../../../includes/vbtecdlinq-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="695e8-105">The SqlMetal command-line tool generates code and mapping for the [!INCLUDE[vbtecdlinq](../../../includes/vbtecdlinq-md.md)] component of the .NET Framework.</span></span> <span data-ttu-id="695e8-106">Bu konunun ilerisinde görünen seçenekleri uygulayarak, SqlMetal'den aşağıdakileri içeren çeşitli farklı eylemler gerçekleştirmesini isteyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="695e8-106">By applying options that appear later in this topic, you can instruct SqlMetal to perform several different actions that include the following:</span></span>  
  
- <span data-ttu-id="695e8-107">Bir veritabanından, kaynak kodu ve eşleme öznitelikleri veya bir eşleme dosyası oluşturmak.</span><span class="sxs-lookup"><span data-stu-id="695e8-107">From a database, generate source code and mapping attributes or a mapping file.</span></span>  
  
- <span data-ttu-id="695e8-108">Bir veritabanından, dosya özelleştirme için bir ara veritabanı işaretleme dili (.dbml) dosyası oluşturmak.</span><span class="sxs-lookup"><span data-stu-id="695e8-108">From a database, generate an intermediate database markup language (.dbml) file for customization.</span></span>  
  
- <span data-ttu-id="695e8-109">Bir .dbml dosyasından, kod veya eşleme öznitelikleri veya bir eşleme dosyası üretmek.</span><span class="sxs-lookup"><span data-stu-id="695e8-109">From a .dbml file, generate code and mapping attributes or a mapping file.</span></span>  
  
 <span data-ttu-id="695e8-110">Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir.</span><span class="sxs-lookup"><span data-stu-id="695e8-110">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="695e8-111">Varsayılan olarak, dosya şu konumda bulunur `drive` : \Program Files\Microsoft SDKs\Windows\v `n.nn` \Bin.</span><span class="sxs-lookup"><span data-stu-id="695e8-111">By default, the file is located at `drive`:\Program Files\Microsoft SDKs\Windows\v`n.nn`\bin.</span></span> <span data-ttu-id="695e8-112">Visual Studio 'Yu yüklemezseniz, [Windows SDK](https://go.microsoft.com/fwlink/?LinkId=142225)Indirerek SqlMetal dosyasını da alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="695e8-112">If you do not install Visual Studio, you can also get the SQLMetal file by downloading the [Windows SDK](https://go.microsoft.com/fwlink/?LinkId=142225).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="695e8-113">Visual Studio kullanan geliştiriciler de Nesne İlişkisel Tasarımcısı varlık sınıfları oluşturmak için kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="695e8-113">Developers who use Visual Studio can also use the Object Relational Designer to generate entity classes.</span></span> <span data-ttu-id="695e8-114">Komut satırı yaklaşımı, büyük veritabanları için uygun düşmektedir.</span><span class="sxs-lookup"><span data-stu-id="695e8-114">The command-line approach scales well for large databases.</span></span> <span data-ttu-id="695e8-115">SqlMetal bir komut satırı aracı olduğundan, bir oluşturma işleminde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="695e8-115">Because SqlMetal is a command-line tool, you can use it in a build process.</span></span>  
  
 <span data-ttu-id="695e8-116">Aracı çalıştırmak için, Visual Studio için Geliştirici Komut İstemi (veya Windows 7 ' de Visual Studio komut Istemi) kullanın.</span><span class="sxs-lookup"><span data-stu-id="695e8-116">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="695e8-117">Daha fazla bilgi için bkz. [komut istemleri](developer-command-prompt-for-vs.md). Komut isteminde aşağıdakileri yazın:</span><span class="sxs-lookup"><span data-stu-id="695e8-117">For more information, see [Command Prompts](developer-command-prompt-for-vs.md).At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="695e8-118">Syntax</span><span class="sxs-lookup"><span data-stu-id="695e8-118">Syntax</span></span>  
  
```console  
sqlmetal [options] [<input file>]  
```  
  
## <a name="options"></a><span data-ttu-id="695e8-119">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="695e8-119">Options</span></span>  
 <span data-ttu-id="695e8-120">En güncel seçenek listesini görüntülemek için, `sqlmetal /?` yüklü konumdan bir komut istemine yazın.</span><span class="sxs-lookup"><span data-stu-id="695e8-120">To view the most current option list, type `sqlmetal /?` at a command prompt from the installed location.</span></span>  
  
 <span data-ttu-id="695e8-121">**Bağlantı seçenekleri**</span><span class="sxs-lookup"><span data-stu-id="695e8-121">**Connection Options**</span></span>  
  
|<span data-ttu-id="695e8-122">Seçenek</span><span class="sxs-lookup"><span data-stu-id="695e8-122">Option</span></span>|<span data-ttu-id="695e8-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="695e8-123">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="695e8-124">\**/Server:\*\*\*\<name>*</span><span class="sxs-lookup"><span data-stu-id="695e8-124">**/server:** *\<name>*</span></span>|<span data-ttu-id="695e8-125">Veritabanı sunucusu adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="695e8-125">Specifies database server name.</span></span>|  
|<span data-ttu-id="695e8-126">\**/Database:\*\*\*\<name>*</span><span class="sxs-lookup"><span data-stu-id="695e8-126">**/database:** *\<name>*</span></span>|<span data-ttu-id="695e8-127">Sunucuda veritabanı kataloğu belirtir.</span><span class="sxs-lookup"><span data-stu-id="695e8-127">Specifies database catalog on server.</span></span>|  
|<span data-ttu-id="695e8-128">\**/User:\*\*\*\<name>*</span><span class="sxs-lookup"><span data-stu-id="695e8-128">**/user:** *\<name>*</span></span>|<span data-ttu-id="695e8-129">Oturum açma kullanıcı kimliğini belirtir. Varsayılan değer: Windows kimlik doğrulamasını kullanın.</span><span class="sxs-lookup"><span data-stu-id="695e8-129">Specifies logon user id. Default value: Use Windows authentication.</span></span>|  
|<span data-ttu-id="695e8-130">\**/Password:\*\*\*\<password>*</span><span class="sxs-lookup"><span data-stu-id="695e8-130">**/password:** *\<password>*</span></span>|<span data-ttu-id="695e8-131">Oturum açma parolasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="695e8-131">Specifies logon password.</span></span> <span data-ttu-id="695e8-132">Varsayılan değer: Windows kimlik doğrulaması kullan.</span><span class="sxs-lookup"><span data-stu-id="695e8-132">Default value: Use Windows authentication.</span></span>|  
|<span data-ttu-id="695e8-133">\**/Conn:\*\*\*\<connection string>*</span><span class="sxs-lookup"><span data-stu-id="695e8-133">**/conn:** *\<connection string>*</span></span>|<span data-ttu-id="695e8-134">Veritabanı bağlantısı dizesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="695e8-134">Specifies database connection string.</span></span> <span data-ttu-id="695e8-135">**/Server**, **/Database**, **/User**veya **/Password** seçenekleriyle birlikte kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="695e8-135">Cannot be used with **/server**, **/database**, **/user**, or **/password** options.</span></span><br /><br /> <span data-ttu-id="695e8-136">Dosya adını bağlantı dizesine eklemeyin.</span><span class="sxs-lookup"><span data-stu-id="695e8-136">Do not include the file name in the connection string.</span></span> <span data-ttu-id="695e8-137">Bunun yerine, dosya adını giriş dosyası olarak komut satırına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="695e8-137">Instead, add the file name to the command line as the input file.</span></span> <span data-ttu-id="695e8-138">Örneğin, aşağıdaki satır giriş dosyası olarak "c:\kuzeydoğu WND.mdf" belirtir: **SqlMetal/Code: "c:\Northwind.cs"/Language: CSharp "c:\kuzeydoğu WND.mdf"**.</span><span class="sxs-lookup"><span data-stu-id="695e8-138">For example, the following line specifies "c:\northwnd.mdf" as the input file: **sqlmetal /code:"c:\northwind.cs" /language:csharp "c:\northwnd.mdf"**.</span></span>|  
|<span data-ttu-id="695e8-139">\**/Timeout:\*\*\*\<seconds>*</span><span class="sxs-lookup"><span data-stu-id="695e8-139">**/timeout:** *\<seconds>*</span></span>|<span data-ttu-id="695e8-140">SqlMetal veritabanına eriştiğinde, zaman aşımı değerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="695e8-140">Specifies time-out value when SqlMetal accesses the database.</span></span> <span data-ttu-id="695e8-141">Varsayılan değer: 0 (yani, zaman sınırı yok).</span><span class="sxs-lookup"><span data-stu-id="695e8-141">Default value: 0 (that is, no time limit).</span></span>|  
  
 <span data-ttu-id="695e8-142">**Ayıklama seçenekleri**</span><span class="sxs-lookup"><span data-stu-id="695e8-142">**Extraction options**</span></span>  
  
|<span data-ttu-id="695e8-143">Seçenek</span><span class="sxs-lookup"><span data-stu-id="695e8-143">Option</span></span>|<span data-ttu-id="695e8-144">Açıklama</span><span class="sxs-lookup"><span data-stu-id="695e8-144">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="695e8-145">**/views**</span><span class="sxs-lookup"><span data-stu-id="695e8-145">**/views**</span></span>|<span data-ttu-id="695e8-146">Veritabanı görünümlerini ayıklar.</span><span class="sxs-lookup"><span data-stu-id="695e8-146">Extracts database views.</span></span>|  
|<span data-ttu-id="695e8-147">**/Functions**</span><span class="sxs-lookup"><span data-stu-id="695e8-147">**/functions**</span></span>|<span data-ttu-id="695e8-148">Veritabanı işlevlerini ayıklar.</span><span class="sxs-lookup"><span data-stu-id="695e8-148">Extracts database functions.</span></span>|  
|<span data-ttu-id="695e8-149">**/sprocs**</span><span class="sxs-lookup"><span data-stu-id="695e8-149">**/sprocs**</span></span>|<span data-ttu-id="695e8-150">Saklı yordamları ayıklar.</span><span class="sxs-lookup"><span data-stu-id="695e8-150">Extracts stored procedures.</span></span>|  
  
 <span data-ttu-id="695e8-151">**Çıkış seçenekleri**</span><span class="sxs-lookup"><span data-stu-id="695e8-151">**Output options**</span></span>  
  
|<span data-ttu-id="695e8-152">Seçenek</span><span class="sxs-lookup"><span data-stu-id="695e8-152">Option</span></span>|<span data-ttu-id="695e8-153">Açıklama</span><span class="sxs-lookup"><span data-stu-id="695e8-153">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="695e8-154">**/DBML** *[: dosya]*</span><span class="sxs-lookup"><span data-stu-id="695e8-154">**/dbml** *[:file]*</span></span>|<span data-ttu-id="695e8-155">Çıkışı .dbml olarak gönderir.</span><span class="sxs-lookup"><span data-stu-id="695e8-155">Sends output as .dbml.</span></span> <span data-ttu-id="695e8-156">**/Map** seçeneğiyle birlikte kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="695e8-156">Cannot be used with **/map** option.</span></span>|  
|<span data-ttu-id="695e8-157">**/Code** *[: File]*</span><span class="sxs-lookup"><span data-stu-id="695e8-157">**/code** *[:file]*</span></span>|<span data-ttu-id="695e8-158">Çıkışı kaynak kodu olarak gönderir.</span><span class="sxs-lookup"><span data-stu-id="695e8-158">Sends output as source code.</span></span> <span data-ttu-id="695e8-159">**/DBML** seçeneğiyle birlikte kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="695e8-159">Cannot be used with **/dbml** option.</span></span>|  
|<span data-ttu-id="695e8-160">**/Map** *[: dosya]*</span><span class="sxs-lookup"><span data-stu-id="695e8-160">**/map** *[:file]*</span></span>|<span data-ttu-id="695e8-161">Öznitelikler yerine bir XML eşleme dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="695e8-161">Generates an XML mapping file instead of attributes.</span></span> <span data-ttu-id="695e8-162">**/DBML** seçeneğiyle birlikte kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="695e8-162">Cannot be used with **/dbml** option.</span></span>|  
  
 <span data-ttu-id="695e8-163">**Çeşitli**</span><span class="sxs-lookup"><span data-stu-id="695e8-163">**Miscellaneous**</span></span>  
  
|<span data-ttu-id="695e8-164">Seçenek</span><span class="sxs-lookup"><span data-stu-id="695e8-164">Option</span></span>|<span data-ttu-id="695e8-165">Açıklama</span><span class="sxs-lookup"><span data-stu-id="695e8-165">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="695e8-166">\**/Language:\*\*\*\<language>*</span><span class="sxs-lookup"><span data-stu-id="695e8-166">**/language:** *\<language>*</span></span>|<span data-ttu-id="695e8-167">Kaynak kod dilini belirtir.</span><span class="sxs-lookup"><span data-stu-id="695e8-167">Specifies source code language.</span></span><br /><br /> <span data-ttu-id="695e8-168">Geçerli *\<language>* : vb, CSharp.</span><span class="sxs-lookup"><span data-stu-id="695e8-168">Valid *\<language>*: vb, csharp.</span></span><br /><br /> <span data-ttu-id="695e8-169">Varsayılan değer: Kod dosyası adındaki uzantıdan türetilir.</span><span class="sxs-lookup"><span data-stu-id="695e8-169">Default value: Derived from extension on code file name.</span></span>|  
|<span data-ttu-id="695e8-170">\**/Namespace:\*\*\*\<name>*</span><span class="sxs-lookup"><span data-stu-id="695e8-170">**/namespace:** *\<name>*</span></span>|<span data-ttu-id="695e8-171">Üretilen kodun ad alanını belirtir.</span><span class="sxs-lookup"><span data-stu-id="695e8-171">Specifies namespace of the generated code.</span></span> <span data-ttu-id="695e8-172">Varsayılan değer: ad alanı yok.</span><span class="sxs-lookup"><span data-stu-id="695e8-172">Default value: no namespace.</span></span>|  
|<span data-ttu-id="695e8-173">\**/Context:\*\*\*\<type>*</span><span class="sxs-lookup"><span data-stu-id="695e8-173">**/context:** *\<type>*</span></span>|<span data-ttu-id="695e8-174">Veri bağlamı sınıfının adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="695e8-174">Specifies name of data context class.</span></span> <span data-ttu-id="695e8-175">Varsayılan değer: Veritabanı adından türetilir.</span><span class="sxs-lookup"><span data-stu-id="695e8-175">Default value: Derived from database name.</span></span>|  
|<span data-ttu-id="695e8-176">\**/entitybase:\*\*\*\<type>*</span><span class="sxs-lookup"><span data-stu-id="695e8-176">**/entitybase:** *\<type>*</span></span>|<span data-ttu-id="695e8-177">Üretilen kodda varlık sınıflarının temel sınıfını belirtir.</span><span class="sxs-lookup"><span data-stu-id="695e8-177">Specifies the base class of the entity classes in the generated code.</span></span> <span data-ttu-id="695e8-178">Varsayılan değer: Varlıkların temel sınıfı yoktur.</span><span class="sxs-lookup"><span data-stu-id="695e8-178">Default value: Entities have no base class.</span></span>|  
|<span data-ttu-id="695e8-179">**/plurleştir**</span><span class="sxs-lookup"><span data-stu-id="695e8-179">**/pluralize**</span></span>|<span data-ttu-id="695e8-180">Sınıf ve üye adlarını otomatik olarak çoğullaştırır veya tekilleştirir.</span><span class="sxs-lookup"><span data-stu-id="695e8-180">Automatically pluralizes or singularizes class and member names.</span></span><br /><br /> <span data-ttu-id="695e8-181">Bu seçenek yalnızca ABD İngilizcesi sürümünde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="695e8-181">This option is available only in the U.S. English version.</span></span>|  
|<span data-ttu-id="695e8-182">\**/Serialization:\*\*\*\<option>*</span><span class="sxs-lookup"><span data-stu-id="695e8-182">**/serialization:** *\<option>*</span></span>|<span data-ttu-id="695e8-183">Seri hale getirilebilir sınıflar oluşturur.</span><span class="sxs-lookup"><span data-stu-id="695e8-183">Generates serializable classes.</span></span><br /><br /> <span data-ttu-id="695e8-184">Geçerli *\<option>* : None, tek yönlü.</span><span class="sxs-lookup"><span data-stu-id="695e8-184">Valid *\<option>*: None, Unidirectional.</span></span> <span data-ttu-id="695e8-185">Varsayılan değer: Hiçbiri.</span><span class="sxs-lookup"><span data-stu-id="695e8-185">Default value: None.</span></span><br /><br /> <span data-ttu-id="695e8-186">Daha fazla bilgi için bkz. [serileştirme](../data/adonet/sql/linq/serialization.md).</span><span class="sxs-lookup"><span data-stu-id="695e8-186">For more information, see [Serialization](../data/adonet/sql/linq/serialization.md).</span></span>|  
  
 <span data-ttu-id="695e8-187">**Giriş Dosyası**</span><span class="sxs-lookup"><span data-stu-id="695e8-187">**Input File**</span></span>  
  
|<span data-ttu-id="695e8-188">Seçenek</span><span class="sxs-lookup"><span data-stu-id="695e8-188">Option</span></span>|<span data-ttu-id="695e8-189">Açıklama</span><span class="sxs-lookup"><span data-stu-id="695e8-189">Description</span></span>|  
|------------|-----------------|  
|**\<input file>**|<span data-ttu-id="695e8-190">Bir SQL Server Express. mdf dosyası, bir SQL Server Compact 3,5. sdf dosyası veya. dbml ara dosyası belirtir.</span><span class="sxs-lookup"><span data-stu-id="695e8-190">Specifies a SQL Server Express .mdf file, a SQL Server Compact 3.5 .sdf file, or a .dbml intermediate file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="695e8-191">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="695e8-191">Remarks</span></span>  
 <span data-ttu-id="695e8-192">SqlMetal işlevi aslında iki adımdan oluşur:</span><span class="sxs-lookup"><span data-stu-id="695e8-192">SqlMetal functionality actually involves two steps:</span></span>  
  
- <span data-ttu-id="695e8-193">Veritabanını meta verilerini bir .dbml dosyasına ayıklama.</span><span class="sxs-lookup"><span data-stu-id="695e8-193">Extracting the metadata of the database into a .dbml file.</span></span>  
  
- <span data-ttu-id="695e8-194">Kod çıktı dosyası oluşturma.</span><span class="sxs-lookup"><span data-stu-id="695e8-194">Generating a code output file.</span></span>  
  
     <span data-ttu-id="695e8-195">Uygun komut satırı seçeneklerini kullanarak Visual Basic veya C# kaynak kodu oluşturabilir veya bir XML eşleme dosyası üretebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="695e8-195">By using the appropriate command-line options, you can produce Visual Basic or C# source code, or you can produce an XML mapping file.</span></span>  
  
 <span data-ttu-id="695e8-196">Meta verileri bir .mdf dosyasından ayıklamak için, .mdf dosyası adını tüm diğer seçeneklerden sonra belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="695e8-196">To extract the metadata from an .mdf file, you must specify the name of the .mdf file after all other options.</span></span>  
  
 <span data-ttu-id="695e8-197">**/Server** belirtilmemişse, **localhost/sqlexpress** varsayılır.</span><span class="sxs-lookup"><span data-stu-id="695e8-197">If no **/server** is specified, **localhost/sqlexpress** is assumed.</span></span>  
  
 <span data-ttu-id="695e8-198">Microsoft SQL Server 2005 aşağıdaki koşullardan biri veya daha fazlası doğru ise bir özel durum oluşturur:</span><span class="sxs-lookup"><span data-stu-id="695e8-198">Microsoft SQL Server 2005 throws an exception if one or more of the following conditions are true:</span></span>  
  
- <span data-ttu-id="695e8-199">SqlMetal, kendi kendini çağıran bir saklı yordam ayıklamaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="695e8-199">SqlMetal tries to extract a stored procedure that calls itself.</span></span>  
  
- <span data-ttu-id="695e8-200">Bir saklı yordam, işlev veya görünümün iç içe geçme düzeyini 32'yi aşıyor.</span><span class="sxs-lookup"><span data-stu-id="695e8-200">The nesting level of a stored procedure, function, or view exceeds 32.</span></span>  
  
     <span data-ttu-id="695e8-201">SqlMetal, bu özel durumu yakalar ve bir uyarı olarak bildirir.</span><span class="sxs-lookup"><span data-stu-id="695e8-201">SqlMetal catches this exception and reports it as a warning.</span></span>  
  
 <span data-ttu-id="695e8-202">Bir giriş dosyası adı belirtmek için, adı komut satırına giriş dosyası olarak ekleyin.</span><span class="sxs-lookup"><span data-stu-id="695e8-202">To specify an input file name, add the name to the command line as the input file.</span></span> <span data-ttu-id="695e8-203">Dosya adının bağlantı dizesine dahil edilmesi ( **/Conn** seçeneği kullanılarak) desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="695e8-203">Including the file name in the connection string (using the **/conn** option) is not supported.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="695e8-204">Örnekler</span><span class="sxs-lookup"><span data-stu-id="695e8-204">Examples</span></span>  
 <span data-ttu-id="695e8-205">Ayıklanan SQL meta verileri içeren bir .dbml dosyası oluşturun:</span><span class="sxs-lookup"><span data-stu-id="695e8-205">Generate a .dbml file that includes extracted SQL metadata:</span></span>  
  
 <span data-ttu-id="695e8-206">**SqlMetal/Server: sunucum/veritabanı: Northwind/DBML: mymeta. dbml**</span><span class="sxs-lookup"><span data-stu-id="695e8-206">**sqlmetal /server:myserver /database:northwind /dbml:mymeta.dbml**</span></span>  
  
 <span data-ttu-id="695e8-207">SQL Server Express kullanarak bir .mdf dosyasından ayıklanan SQL meta verilerini içeren bir .dbml dosyası oluşturun:</span><span class="sxs-lookup"><span data-stu-id="695e8-207">Generate a .dbml file that includes extracted SQL metadata from an .mdf file by using SQL Server Express:</span></span>  
  
 <span data-ttu-id="695e8-208">**SqlMetal/DBML: mymeta. dbml mydbfile. mdf**</span><span class="sxs-lookup"><span data-stu-id="695e8-208">**sqlmetal /dbml:mymeta.dbml mydbfile.mdf**</span></span>  
  
 <span data-ttu-id="695e8-209">SQL Server Express'ten ayıklanan SQL meta verilerini içeren bir .dbml dosyası oluşturun:</span><span class="sxs-lookup"><span data-stu-id="695e8-209">Generate a .dbml file that includes extracted SQL metadata from SQL Server Express:</span></span>  
  
 <span data-ttu-id="695e8-210">**SqlMetal/Server: .\SQLEXPRESS/DBML: mymeta. dbml/Database: Northwind**</span><span class="sxs-lookup"><span data-stu-id="695e8-210">**sqlmetal /server:.\sqlexpress /dbml:mymeta.dbml /database:northwind**</span></span>  
  
 <span data-ttu-id="695e8-211">Dbml meta veri dosyasından kaynak kodu oluşturun:</span><span class="sxs-lookup"><span data-stu-id="695e8-211">Generate source code from a .dbml metadata file:</span></span>  
  
 <span data-ttu-id="695e8-212">**SqlMetal/Namespace: Nwind/Code: nrüzgar. cs/Language: CSharp mymetal. dbml**</span><span class="sxs-lookup"><span data-stu-id="695e8-212">**sqlmetal /namespace:nwind /code:nwind.cs /language:csharp mymetal.dbml**</span></span>  
  
 <span data-ttu-id="695e8-213">Doğrudan SQL meta verilerinden kaynak kodu oluşturun:</span><span class="sxs-lookup"><span data-stu-id="695e8-213">Generate source code from SQL metadata directly:</span></span>  
  
 <span data-ttu-id="695e8-214">**SqlMetal/Server: sunucum/veritabanı: Northwind/Namespace: Nwind/Code: nrüzgar. cs/Language: CSharp**</span><span class="sxs-lookup"><span data-stu-id="695e8-214">**sqlmetal /server:myserver /database:northwind /namespace:nwind /code:nwind.cs /language:csharp**</span></span>  
  
> [!NOTE]
> <span data-ttu-id="695e8-215">Northwind örnek veritabanıyla **/plurleştir** seçeneğini kullandığınızda aşağıdaki davranışa göz önünde bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="695e8-215">When you use the **/pluralize** option with the Northwind sample database, note the following behavior.</span></span> <span data-ttu-id="695e8-216">SqlMetal tablolar için satır türünde adlar oluşturduğunda, tablo adları tekildir.</span><span class="sxs-lookup"><span data-stu-id="695e8-216">When SqlMetal makes row-type names for tables, the table names are singular.</span></span> <span data-ttu-id="695e8-217"><xref:System.Data.Linq.DataContext>Tablolar için özellikler yaptığında tablo adları plural olur.</span><span class="sxs-lookup"><span data-stu-id="695e8-217">When it makes <xref:System.Data.Linq.DataContext> properties for tables, the table names are plural.</span></span> <span data-ttu-id="695e8-218">Tesadüfen, Northwind örnek veritabanındaki tablolar zaten çoğuldur.</span><span class="sxs-lookup"><span data-stu-id="695e8-218">Coincidentally, the tables in the Northwind sample database are already plural.</span></span> <span data-ttu-id="695e8-219">Bu nedenle, bu bölümün çalıştığını görmezsiniz.</span><span class="sxs-lookup"><span data-stu-id="695e8-219">Therefore, you do not see that part working.</span></span> <span data-ttu-id="695e8-220">Veritabanı tablolarını tekil olarak adlandırmak ortak uygulama olsa da, toplulukları çoğul olarak adlandırmak da .NET'te ortak bir uygulamadır.</span><span class="sxs-lookup"><span data-stu-id="695e8-220">Although it is common practice to name database tables singular, it is also a common practice in .NET to name collections plural.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="695e8-221">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="695e8-221">See also</span></span>

- [<span data-ttu-id="695e8-222">Nasıl yapılır: Visual Basic veya C# içinde Nesne Modeli Oluşturma</span><span class="sxs-lookup"><span data-stu-id="695e8-222">How to: Generate the Object Model in Visual Basic or C#</span></span>](../data/adonet/sql/linq/how-to-generate-the-object-model-in-visual-basic-or-csharp.md)
- [<span data-ttu-id="695e8-223">LINQ to SQL’de Kod Oluşturma</span><span class="sxs-lookup"><span data-stu-id="695e8-223">Code Generation in LINQ to SQL</span></span>](../data/adonet/sql/linq/code-generation-in-linq-to-sql.md)
- [<span data-ttu-id="695e8-224">Dış Eşleme</span><span class="sxs-lookup"><span data-stu-id="695e8-224">External Mapping</span></span>](../data/adonet/sql/linq/external-mapping.md)
