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
ms.openlocfilehash: 57229ce767a140e1756fddb2c19fb31893a0ab90
ms.sourcegitcommit: 1dbe25ff484a02025d5c34146e517c236f7161fb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/19/2021
ms.locfileid: "104653627"
---
# <a name="sqlmetalexe-code-generation-tool"></a><span data-ttu-id="99869-104">SqlMetal.exe (Kod Üretme Aracı)</span><span class="sxs-lookup"><span data-stu-id="99869-104">SqlMetal.exe (Code Generation Tool)</span></span>

<span data-ttu-id="99869-105">SqlMetal komut satırı aracı .NET Framework bileşeni için kod ve eşleme oluşturur [!INCLUDE[vbtecdlinq](../../../includes/vbtecdlinq-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="99869-105">The SqlMetal command-line tool generates code and mapping for the [!INCLUDE[vbtecdlinq](../../../includes/vbtecdlinq-md.md)] component of the .NET Framework.</span></span> <span data-ttu-id="99869-106">Bu konunun ilerisinde görünen seçenekleri uygulayarak, SqlMetal'den aşağıdakileri içeren çeşitli farklı eylemler gerçekleştirmesini isteyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="99869-106">By applying options that appear later in this topic, you can instruct SqlMetal to perform several different actions that include the following:</span></span>  
  
- <span data-ttu-id="99869-107">Bir veritabanından, kaynak kodu ve eşleme öznitelikleri veya bir eşleme dosyası oluşturmak.</span><span class="sxs-lookup"><span data-stu-id="99869-107">From a database, generate source code and mapping attributes or a mapping file.</span></span>  
  
- <span data-ttu-id="99869-108">Bir veritabanından, dosya özelleştirme için bir ara veritabanı işaretleme dili (.dbml) dosyası oluşturmak.</span><span class="sxs-lookup"><span data-stu-id="99869-108">From a database, generate an intermediate database markup language (.dbml) file for customization.</span></span>  
  
- <span data-ttu-id="99869-109">Bir .dbml dosyasından, kod veya eşleme öznitelikleri veya bir eşleme dosyası üretmek.</span><span class="sxs-lookup"><span data-stu-id="99869-109">From a .dbml file, generate code and mapping attributes or a mapping file.</span></span>  
  
<span data-ttu-id="99869-110">Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir.</span><span class="sxs-lookup"><span data-stu-id="99869-110">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="99869-111">Varsayılan olarak, dosya şu konumda bulunur `drive` : \Program Files\Microsoft SDKs\Windows\v `n.nn` \Bin.</span><span class="sxs-lookup"><span data-stu-id="99869-111">By default, the file is located at `drive`:\Program Files\Microsoft SDKs\Windows\v`n.nn`\bin.</span></span> <span data-ttu-id="99869-112">Visual Studio 'Yu yüklemezseniz, [Windows SDK](https://go.microsoft.com/fwlink/?LinkId=142225)Indirerek SqlMetal dosyasını da alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="99869-112">If you do not install Visual Studio, you can also get the SQLMetal file by downloading the [Windows SDK](https://go.microsoft.com/fwlink/?LinkId=142225).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="99869-113">Visual Studio kullanan geliştiriciler de Nesne İlişkisel Tasarımcısı varlık sınıfları oluşturmak için kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="99869-113">Developers who use Visual Studio can also use the Object Relational Designer to generate entity classes.</span></span> <span data-ttu-id="99869-114">Komut satırı yaklaşımı, büyük veritabanları için uygun düşmektedir.</span><span class="sxs-lookup"><span data-stu-id="99869-114">The command-line approach scales well for large databases.</span></span> <span data-ttu-id="99869-115">SqlMetal bir komut satırı aracı olduğundan, bir oluşturma işleminde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="99869-115">Because SqlMetal is a command-line tool, you can use it in a build process.</span></span>  
  
<span data-ttu-id="99869-116">Aracı çalıştırmak için [Visual studio Geliştirici komut istemi veya Visual Studio Geliştirici PowerShell](/visualstudio/ide/reference/command-prompt-powershell)kullanın.</span><span class="sxs-lookup"><span data-stu-id="99869-116">To run the tool, use [Visual Studio Developer Command Prompt or Visual Studio Developer PowerShell](/visualstudio/ide/reference/command-prompt-powershell).</span></span> <span data-ttu-id="99869-117">Komut isteminde aşağıdaki komutu girin:</span><span class="sxs-lookup"><span data-stu-id="99869-117">At the command prompt, enter the following command:</span></span>

```console  
sqlmetal [options] [<input file>]  
```  
  
## <a name="options"></a><span data-ttu-id="99869-118">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="99869-118">Options</span></span>  

 <span data-ttu-id="99869-119">En güncel seçenek listesini görüntülemek için, `sqlmetal /?` yüklü konumdan bir komut istemine yazın.</span><span class="sxs-lookup"><span data-stu-id="99869-119">To view the most current option list, type `sqlmetal /?` at a command prompt from the installed location.</span></span>  
  
 <span data-ttu-id="99869-120">**Bağlantı seçenekleri**</span><span class="sxs-lookup"><span data-stu-id="99869-120">**Connection Options**</span></span>  
  
|<span data-ttu-id="99869-121">Seçenek</span><span class="sxs-lookup"><span data-stu-id="99869-121">Option</span></span>|<span data-ttu-id="99869-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="99869-122">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="99869-123">\**/Server:\*\*\*\<name>*</span><span class="sxs-lookup"><span data-stu-id="99869-123">**/server:** *\<name>*</span></span>|<span data-ttu-id="99869-124">Veritabanı sunucusu adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="99869-124">Specifies database server name.</span></span>|  
|<span data-ttu-id="99869-125">\**/Database:\*\*\*\<name>*</span><span class="sxs-lookup"><span data-stu-id="99869-125">**/database:** *\<name>*</span></span>|<span data-ttu-id="99869-126">Sunucuda veritabanı kataloğu belirtir.</span><span class="sxs-lookup"><span data-stu-id="99869-126">Specifies database catalog on server.</span></span>|  
|<span data-ttu-id="99869-127">\**/User:\*\*\*\<name>*</span><span class="sxs-lookup"><span data-stu-id="99869-127">**/user:** *\<name>*</span></span>|<span data-ttu-id="99869-128">Oturum açma kullanıcı kimliğini belirtir. Varsayılan değer: Windows kimlik doğrulamasını kullanın.</span><span class="sxs-lookup"><span data-stu-id="99869-128">Specifies logon user id. Default value: Use Windows authentication.</span></span>|  
|<span data-ttu-id="99869-129">\**/Password:\*\*\*\<password>*</span><span class="sxs-lookup"><span data-stu-id="99869-129">**/password:** *\<password>*</span></span>|<span data-ttu-id="99869-130">Oturum açma parolasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="99869-130">Specifies logon password.</span></span> <span data-ttu-id="99869-131">Varsayılan değer: Windows kimlik doğrulaması kullan.</span><span class="sxs-lookup"><span data-stu-id="99869-131">Default value: Use Windows authentication.</span></span>|  
|<span data-ttu-id="99869-132">\**/Conn:\*\*\*\<connection string>*</span><span class="sxs-lookup"><span data-stu-id="99869-132">**/conn:** *\<connection string>*</span></span>|<span data-ttu-id="99869-133">Veritabanı bağlantısı dizesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="99869-133">Specifies database connection string.</span></span> <span data-ttu-id="99869-134">**/Server**, **/Database**, **/User** veya **/Password** seçenekleriyle birlikte kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="99869-134">Cannot be used with **/server**, **/database**, **/user**, or **/password** options.</span></span><br /><br /> <span data-ttu-id="99869-135">Dosya adını bağlantı dizesine eklemeyin.</span><span class="sxs-lookup"><span data-stu-id="99869-135">Do not include the file name in the connection string.</span></span> <span data-ttu-id="99869-136">Bunun yerine, dosya adını giriş dosyası olarak komut satırına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="99869-136">Instead, add the file name to the command line as the input file.</span></span> <span data-ttu-id="99869-137">Örneğin, aşağıdaki satır giriş dosyası olarak "c:\kuzeydoğu WND.mdf" belirtir: **SqlMetal/Code: "c:\Northwind.cs"/Language: CSharp "c:\kuzeydoğu WND.mdf"**.</span><span class="sxs-lookup"><span data-stu-id="99869-137">For example, the following line specifies "c:\northwnd.mdf" as the input file: **sqlmetal /code:"c:\northwind.cs" /language:csharp "c:\northwnd.mdf"**.</span></span>|  
|<span data-ttu-id="99869-138">\**/Timeout:\*\*\*\<seconds>*</span><span class="sxs-lookup"><span data-stu-id="99869-138">**/timeout:** *\<seconds>*</span></span>|<span data-ttu-id="99869-139">SqlMetal veritabanına eriştiğinde, zaman aşımı değerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="99869-139">Specifies time-out value when SqlMetal accesses the database.</span></span> <span data-ttu-id="99869-140">Varsayılan değer: 0 (yani, zaman sınırı yok).</span><span class="sxs-lookup"><span data-stu-id="99869-140">Default value: 0 (that is, no time limit).</span></span>|  
  
 <span data-ttu-id="99869-141">**Ayıklama seçenekleri**</span><span class="sxs-lookup"><span data-stu-id="99869-141">**Extraction options**</span></span>  
  
|<span data-ttu-id="99869-142">Seçenek</span><span class="sxs-lookup"><span data-stu-id="99869-142">Option</span></span>|<span data-ttu-id="99869-143">Açıklama</span><span class="sxs-lookup"><span data-stu-id="99869-143">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="99869-144">**/views**</span><span class="sxs-lookup"><span data-stu-id="99869-144">**/views**</span></span>|<span data-ttu-id="99869-145">Veritabanı görünümlerini ayıklar.</span><span class="sxs-lookup"><span data-stu-id="99869-145">Extracts database views.</span></span>|  
|<span data-ttu-id="99869-146">**/Functions**</span><span class="sxs-lookup"><span data-stu-id="99869-146">**/functions**</span></span>|<span data-ttu-id="99869-147">Veritabanı işlevlerini ayıklar.</span><span class="sxs-lookup"><span data-stu-id="99869-147">Extracts database functions.</span></span>|  
|<span data-ttu-id="99869-148">**/sprocs**</span><span class="sxs-lookup"><span data-stu-id="99869-148">**/sprocs**</span></span>|<span data-ttu-id="99869-149">Saklı yordamları ayıklar.</span><span class="sxs-lookup"><span data-stu-id="99869-149">Extracts stored procedures.</span></span>|  
  
 <span data-ttu-id="99869-150">**Çıkış seçenekleri**</span><span class="sxs-lookup"><span data-stu-id="99869-150">**Output options**</span></span>  
  
|<span data-ttu-id="99869-151">Seçenek</span><span class="sxs-lookup"><span data-stu-id="99869-151">Option</span></span>|<span data-ttu-id="99869-152">Açıklama</span><span class="sxs-lookup"><span data-stu-id="99869-152">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="99869-153">**/DBML** *[: dosya]*</span><span class="sxs-lookup"><span data-stu-id="99869-153">**/dbml** *[:file]*</span></span>|<span data-ttu-id="99869-154">Çıkışı .dbml olarak gönderir.</span><span class="sxs-lookup"><span data-stu-id="99869-154">Sends output as .dbml.</span></span> <span data-ttu-id="99869-155">**/Map** seçeneğiyle birlikte kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="99869-155">Cannot be used with **/map** option.</span></span>|  
|<span data-ttu-id="99869-156">**/Code** *[: File]*</span><span class="sxs-lookup"><span data-stu-id="99869-156">**/code** *[:file]*</span></span>|<span data-ttu-id="99869-157">Çıkışı kaynak kodu olarak gönderir.</span><span class="sxs-lookup"><span data-stu-id="99869-157">Sends output as source code.</span></span> <span data-ttu-id="99869-158">**/DBML** seçeneğiyle birlikte kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="99869-158">Cannot be used with **/dbml** option.</span></span>|  
|<span data-ttu-id="99869-159">**/Map** *[: dosya]*</span><span class="sxs-lookup"><span data-stu-id="99869-159">**/map** *[:file]*</span></span>|<span data-ttu-id="99869-160">Öznitelikler yerine bir XML eşleme dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="99869-160">Generates an XML mapping file instead of attributes.</span></span> <span data-ttu-id="99869-161">**/DBML** seçeneğiyle birlikte kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="99869-161">Cannot be used with **/dbml** option.</span></span>|  
  
 <span data-ttu-id="99869-162">**Çeşitli**</span><span class="sxs-lookup"><span data-stu-id="99869-162">**Miscellaneous**</span></span>  
  
|<span data-ttu-id="99869-163">Seçenek</span><span class="sxs-lookup"><span data-stu-id="99869-163">Option</span></span>|<span data-ttu-id="99869-164">Açıklama</span><span class="sxs-lookup"><span data-stu-id="99869-164">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="99869-165">\**/Language:\*\*\*\<language>*</span><span class="sxs-lookup"><span data-stu-id="99869-165">**/language:** *\<language>*</span></span>|<span data-ttu-id="99869-166">Kaynak kod dilini belirtir.</span><span class="sxs-lookup"><span data-stu-id="99869-166">Specifies source code language.</span></span><br /><br /> <span data-ttu-id="99869-167">Geçerli *\<language>* : vb, CSharp.</span><span class="sxs-lookup"><span data-stu-id="99869-167">Valid *\<language>*: vb, csharp.</span></span><br /><br /> <span data-ttu-id="99869-168">Varsayılan değer: Kod dosyası adındaki uzantıdan türetilir.</span><span class="sxs-lookup"><span data-stu-id="99869-168">Default value: Derived from extension on code file name.</span></span>|  
|<span data-ttu-id="99869-169">\**/Namespace:\*\*\*\<name>*</span><span class="sxs-lookup"><span data-stu-id="99869-169">**/namespace:** *\<name>*</span></span>|<span data-ttu-id="99869-170">Üretilen kodun ad alanını belirtir.</span><span class="sxs-lookup"><span data-stu-id="99869-170">Specifies namespace of the generated code.</span></span> <span data-ttu-id="99869-171">Varsayılan değer: ad alanı yok.</span><span class="sxs-lookup"><span data-stu-id="99869-171">Default value: no namespace.</span></span>|  
|<span data-ttu-id="99869-172">\**/Context:\*\*\*\<type>*</span><span class="sxs-lookup"><span data-stu-id="99869-172">**/context:** *\<type>*</span></span>|<span data-ttu-id="99869-173">Veri bağlamı sınıfının adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="99869-173">Specifies name of data context class.</span></span> <span data-ttu-id="99869-174">Varsayılan değer: Veritabanı adından türetilir.</span><span class="sxs-lookup"><span data-stu-id="99869-174">Default value: Derived from database name.</span></span>|  
|<span data-ttu-id="99869-175">\**/entitybase:\*\*\*\<type>*</span><span class="sxs-lookup"><span data-stu-id="99869-175">**/entitybase:** *\<type>*</span></span>|<span data-ttu-id="99869-176">Üretilen kodda varlık sınıflarının temel sınıfını belirtir.</span><span class="sxs-lookup"><span data-stu-id="99869-176">Specifies the base class of the entity classes in the generated code.</span></span> <span data-ttu-id="99869-177">Varsayılan değer: Varlıkların temel sınıfı yoktur.</span><span class="sxs-lookup"><span data-stu-id="99869-177">Default value: Entities have no base class.</span></span>|  
|<span data-ttu-id="99869-178">**/plurleştir**</span><span class="sxs-lookup"><span data-stu-id="99869-178">**/pluralize**</span></span>|<span data-ttu-id="99869-179">Sınıf ve üye adlarını otomatik olarak çoğullaştırır veya tekilleştirir.</span><span class="sxs-lookup"><span data-stu-id="99869-179">Automatically pluralizes or singularizes class and member names.</span></span><br /><br /> <span data-ttu-id="99869-180">Bu seçenek yalnızca ABD İngilizcesi sürümünde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="99869-180">This option is available only in the U.S. English version.</span></span>|  
|<span data-ttu-id="99869-181">\**/Serialization:\*\*\*\<option>*</span><span class="sxs-lookup"><span data-stu-id="99869-181">**/serialization:** *\<option>*</span></span>|<span data-ttu-id="99869-182">Seri hale getirilebilir sınıflar oluşturur.</span><span class="sxs-lookup"><span data-stu-id="99869-182">Generates serializable classes.</span></span><br /><br /> <span data-ttu-id="99869-183">Geçerli *\<option>* : None, tek yönlü.</span><span class="sxs-lookup"><span data-stu-id="99869-183">Valid *\<option>*: None, Unidirectional.</span></span> <span data-ttu-id="99869-184">Varsayılan değer: Hiçbiri.</span><span class="sxs-lookup"><span data-stu-id="99869-184">Default value: None.</span></span><br /><br /> <span data-ttu-id="99869-185">Daha fazla bilgi için bkz. [serileştirme](../data/adonet/sql/linq/serialization.md).</span><span class="sxs-lookup"><span data-stu-id="99869-185">For more information, see [Serialization](../data/adonet/sql/linq/serialization.md).</span></span>|  
  
 <span data-ttu-id="99869-186">**Giriş Dosyası**</span><span class="sxs-lookup"><span data-stu-id="99869-186">**Input File**</span></span>  
  
|<span data-ttu-id="99869-187">Seçenek</span><span class="sxs-lookup"><span data-stu-id="99869-187">Option</span></span>|<span data-ttu-id="99869-188">Açıklama</span><span class="sxs-lookup"><span data-stu-id="99869-188">Description</span></span>|  
|------------|-----------------|  
|**\<input file>**|<span data-ttu-id="99869-189">Bir SQL Server Express. mdf dosyası, bir SQL Server Compact 3,5. sdf dosyası veya. dbml ara dosyası belirtir.</span><span class="sxs-lookup"><span data-stu-id="99869-189">Specifies a SQL Server Express .mdf file, a SQL Server Compact 3.5 .sdf file, or a .dbml intermediate file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="99869-190">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="99869-190">Remarks</span></span>  

 <span data-ttu-id="99869-191">SqlMetal işlevi aslında iki adımdan oluşur:</span><span class="sxs-lookup"><span data-stu-id="99869-191">SqlMetal functionality actually involves two steps:</span></span>  
  
- <span data-ttu-id="99869-192">Veritabanını meta verilerini bir .dbml dosyasına ayıklama.</span><span class="sxs-lookup"><span data-stu-id="99869-192">Extracting the metadata of the database into a .dbml file.</span></span>  
  
- <span data-ttu-id="99869-193">Kod çıktı dosyası oluşturma.</span><span class="sxs-lookup"><span data-stu-id="99869-193">Generating a code output file.</span></span>  
  
     <span data-ttu-id="99869-194">Uygun komut satırı seçeneklerini kullanarak Visual Basic veya C# kaynak kodu oluşturabilir veya bir XML eşleme dosyası üretebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="99869-194">By using the appropriate command-line options, you can produce Visual Basic or C# source code, or you can produce an XML mapping file.</span></span>  
  
 <span data-ttu-id="99869-195">Meta verileri bir .mdf dosyasından ayıklamak için, .mdf dosyası adını tüm diğer seçeneklerden sonra belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="99869-195">To extract the metadata from an .mdf file, you must specify the name of the .mdf file after all other options.</span></span>  
  
 <span data-ttu-id="99869-196">**/Server** belirtilmemişse, **localhost/sqlexpress** varsayılır.</span><span class="sxs-lookup"><span data-stu-id="99869-196">If no **/server** is specified, **localhost/sqlexpress** is assumed.</span></span>  
  
 <span data-ttu-id="99869-197">Microsoft SQL Server 2005 aşağıdaki koşullardan biri veya daha fazlası doğru ise bir özel durum oluşturur:</span><span class="sxs-lookup"><span data-stu-id="99869-197">Microsoft SQL Server 2005 throws an exception if one or more of the following conditions are true:</span></span>  
  
- <span data-ttu-id="99869-198">SqlMetal, kendi kendini çağıran bir saklı yordam ayıklamaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="99869-198">SqlMetal tries to extract a stored procedure that calls itself.</span></span>  
  
- <span data-ttu-id="99869-199">Bir saklı yordam, işlev veya görünümün iç içe geçme düzeyini 32'yi aşıyor.</span><span class="sxs-lookup"><span data-stu-id="99869-199">The nesting level of a stored procedure, function, or view exceeds 32.</span></span>  
  
     <span data-ttu-id="99869-200">SqlMetal, bu özel durumu yakalar ve bir uyarı olarak bildirir.</span><span class="sxs-lookup"><span data-stu-id="99869-200">SqlMetal catches this exception and reports it as a warning.</span></span>  
  
 <span data-ttu-id="99869-201">Bir giriş dosyası adı belirtmek için, adı komut satırına giriş dosyası olarak ekleyin.</span><span class="sxs-lookup"><span data-stu-id="99869-201">To specify an input file name, add the name to the command line as the input file.</span></span> <span data-ttu-id="99869-202">Dosya adının bağlantı dizesine dahil edilmesi ( **/Conn** seçeneği kullanılarak) desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="99869-202">Including the file name in the connection string (using the **/conn** option) is not supported.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="99869-203">Örnekler</span><span class="sxs-lookup"><span data-stu-id="99869-203">Examples</span></span>  

 <span data-ttu-id="99869-204">Ayıklanan SQL meta verileri içeren bir .dbml dosyası oluşturun:</span><span class="sxs-lookup"><span data-stu-id="99869-204">Generate a .dbml file that includes extracted SQL metadata:</span></span>  
  
 <span data-ttu-id="99869-205">**SqlMetal/Server: sunucum/veritabanı: Northwind/DBML: mymeta. dbml**</span><span class="sxs-lookup"><span data-stu-id="99869-205">**sqlmetal /server:myserver /database:northwind /dbml:mymeta.dbml**</span></span>  
  
 <span data-ttu-id="99869-206">SQL Server Express kullanarak bir .mdf dosyasından ayıklanan SQL meta verilerini içeren bir .dbml dosyası oluşturun:</span><span class="sxs-lookup"><span data-stu-id="99869-206">Generate a .dbml file that includes extracted SQL metadata from an .mdf file by using SQL Server Express:</span></span>  
  
 <span data-ttu-id="99869-207">**SqlMetal/DBML: mymeta. dbml mydbfile. mdf**</span><span class="sxs-lookup"><span data-stu-id="99869-207">**sqlmetal /dbml:mymeta.dbml mydbfile.mdf**</span></span>  
  
 <span data-ttu-id="99869-208">SQL Server Express'ten ayıklanan SQL meta verilerini içeren bir .dbml dosyası oluşturun:</span><span class="sxs-lookup"><span data-stu-id="99869-208">Generate a .dbml file that includes extracted SQL metadata from SQL Server Express:</span></span>  
  
 <span data-ttu-id="99869-209">**SqlMetal/Server: .\SQLEXPRESS/DBML: mymeta. dbml/Database: Northwind**</span><span class="sxs-lookup"><span data-stu-id="99869-209">**sqlmetal /server:.\sqlexpress /dbml:mymeta.dbml /database:northwind**</span></span>  
  
 <span data-ttu-id="99869-210">Dbml meta veri dosyasından kaynak kodu oluşturun:</span><span class="sxs-lookup"><span data-stu-id="99869-210">Generate source code from a .dbml metadata file:</span></span>  
  
 <span data-ttu-id="99869-211">**SqlMetal/Namespace: Nwind/Code: nrüzgar. cs/Language: CSharp mymetal. dbml**</span><span class="sxs-lookup"><span data-stu-id="99869-211">**sqlmetal /namespace:nwind /code:nwind.cs /language:csharp mymetal.dbml**</span></span>  
  
 <span data-ttu-id="99869-212">Doğrudan SQL meta verilerinden kaynak kodu oluşturun:</span><span class="sxs-lookup"><span data-stu-id="99869-212">Generate source code from SQL metadata directly:</span></span>  
  
 <span data-ttu-id="99869-213">**SqlMetal/Server: sunucum/veritabanı: Northwind/Namespace: Nwind/Code: nrüzgar. cs/Language: CSharp**</span><span class="sxs-lookup"><span data-stu-id="99869-213">**sqlmetal /server:myserver /database:northwind /namespace:nwind /code:nwind.cs /language:csharp**</span></span>  
  
> [!NOTE]
> <span data-ttu-id="99869-214">Northwind örnek veritabanıyla **/plurleştir** seçeneğini kullandığınızda aşağıdaki davranışa göz önünde bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="99869-214">When you use the **/pluralize** option with the Northwind sample database, note the following behavior.</span></span> <span data-ttu-id="99869-215">SqlMetal tablolar için satır türünde adlar oluşturduğunda, tablo adları tekildir.</span><span class="sxs-lookup"><span data-stu-id="99869-215">When SqlMetal makes row-type names for tables, the table names are singular.</span></span> <span data-ttu-id="99869-216"><xref:System.Data.Linq.DataContext>Tablolar için özellikler yaptığında tablo adları plural olur.</span><span class="sxs-lookup"><span data-stu-id="99869-216">When it makes <xref:System.Data.Linq.DataContext> properties for tables, the table names are plural.</span></span> <span data-ttu-id="99869-217">Tesadüfen, Northwind örnek veritabanındaki tablolar zaten çoğuldur.</span><span class="sxs-lookup"><span data-stu-id="99869-217">Coincidentally, the tables in the Northwind sample database are already plural.</span></span> <span data-ttu-id="99869-218">Bu nedenle, bu bölümün çalıştığını görmezsiniz.</span><span class="sxs-lookup"><span data-stu-id="99869-218">Therefore, you do not see that part working.</span></span> <span data-ttu-id="99869-219">Veritabanı tablolarını tekil olarak adlandırmak ortak uygulama olsa da, toplulukları çoğul olarak adlandırmak da .NET'te ortak bir uygulamadır.</span><span class="sxs-lookup"><span data-stu-id="99869-219">Although it is common practice to name database tables singular, it is also a common practice in .NET to name collections plural.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99869-220">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="99869-220">See also</span></span>

- [<span data-ttu-id="99869-221">Nasıl yapılır: Visual Basic veya C# içinde Nesne Modeli Oluşturma</span><span class="sxs-lookup"><span data-stu-id="99869-221">How to: Generate the Object Model in Visual Basic or C#</span></span>](../data/adonet/sql/linq/how-to-generate-the-object-model-in-visual-basic-or-csharp.md)
- [<span data-ttu-id="99869-222">LINQ to SQL’de Kod Oluşturma</span><span class="sxs-lookup"><span data-stu-id="99869-222">Code Generation in LINQ to SQL</span></span>](../data/adonet/sql/linq/code-generation-in-linq-to-sql.md)
- [<span data-ttu-id="99869-223">Dış Eşleme</span><span class="sxs-lookup"><span data-stu-id="99869-223">External Mapping</span></span>](../data/adonet/sql/linq/external-mapping.md)
