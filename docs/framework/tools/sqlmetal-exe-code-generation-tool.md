---
title: "SqlMetal.exe (Kod Üretme Aracı)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQLMetal [LINQ to SQL]
- code generation tool
- SQLMetal.exe
- LINQ to SQL, serialization
- LINQ to SQL, DBML files
- LINQ to SQL, SQLMetal
ms.assetid: 819e5a96-7646-4fdb-b14b-fe31221b0614
caps.latest.revision: "43"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: fa4cf7baa3ca3ba19a733438920357034e8de193
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="sqlmetalexe-code-generation-tool"></a><span data-ttu-id="53921-102">SqlMetal.exe (Kod Üretme Aracı)</span><span class="sxs-lookup"><span data-stu-id="53921-102">SqlMetal.exe (Code Generation Tool)</span></span>
<span data-ttu-id="53921-103">Kod ve eşleme için SqlMetal komut satırı aracı oluşturur [!INCLUDE[vbtecdlinq](../../../includes/vbtecdlinq-md.md)] bileşenini [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="53921-103">The SqlMetal command-line tool generates code and mapping for the [!INCLUDE[vbtecdlinq](../../../includes/vbtecdlinq-md.md)] component of the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="53921-104">Bu konunun ilerisinde görünen seçenekleri uygulayarak, SqlMetal'den aşağıdakileri içeren çeşitli farklı eylemler gerçekleştirmesini isteyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="53921-104">By applying options that appear later in this topic, you can instruct SqlMetal to perform several different actions that include the following:</span></span>  
  
-   <span data-ttu-id="53921-105">Bir veritabanından, kaynak kodu ve eşleme öznitelikleri veya bir eşleme dosyası oluşturmak.</span><span class="sxs-lookup"><span data-stu-id="53921-105">From a database, generate source code and mapping attributes or a mapping file.</span></span>  
  
-   <span data-ttu-id="53921-106">Bir veritabanından, dosya özelleştirme için bir ara veritabanı işaretleme dili (.dbml) dosyası oluşturmak.</span><span class="sxs-lookup"><span data-stu-id="53921-106">From a database, generate an intermediate database markup language (.dbml) file for customization.</span></span>  
  
-   <span data-ttu-id="53921-107">Bir .dbml dosyasından, kod veya eşleme öznitelikleri veya bir eşleme dosyası üretmek.</span><span class="sxs-lookup"><span data-stu-id="53921-107">From a .dbml file, generate code and mapping attributes or a mapping file.</span></span>  
  
 <span data-ttu-id="53921-108">Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir.</span><span class="sxs-lookup"><span data-stu-id="53921-108">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="53921-109">Varsayılan olarak, dosyası şu konumdadır `drive`: \Program SDKs\Windows\v`n.nn`\bin.</span><span class="sxs-lookup"><span data-stu-id="53921-109">By default, the file is located at `drive`:\Program Files\Microsoft SDKs\Windows\v`n.nn`\bin.</span></span> <span data-ttu-id="53921-110">Visual Studio yüklemezseniz, ayrıca SQLMetal dosya yükleyerek alabilirsiniz [Windows SDK](http://go.microsoft.com/fwlink/?LinkId=142225).</span><span class="sxs-lookup"><span data-stu-id="53921-110">If you do not install Visual Studio, you can also get the SQLMetal file by downloading the [Windows SDK](http://go.microsoft.com/fwlink/?LinkId=142225).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="53921-111">Visual Studio kullanan geliştiriciler de kullanabilir [!INCLUDE[vs_ordesigner_long](../../../includes/vs-ordesigner-long-md.md)] sınıflar oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="53921-111">Developers who use Visual Studio can also use the [!INCLUDE[vs_ordesigner_long](../../../includes/vs-ordesigner-long-md.md)] to generate entity classes.</span></span> <span data-ttu-id="53921-112">Komut satırı yaklaşımı, büyük veritabanları için uygun düşmektedir.</span><span class="sxs-lookup"><span data-stu-id="53921-112">The command-line approach scales well for large databases.</span></span> <span data-ttu-id="53921-113">SqlMetal bir komut satırı aracı olduğundan, bir oluşturma işleminde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="53921-113">Because SqlMetal is a command-line tool, you can use it in a build process.</span></span>  
  
 <span data-ttu-id="53921-114">Aracı çalıştırmak için, Geliştirici Komut İstemi (veya Windows 7'de Visual Studio Komut İstemi) kullanın.</span><span class="sxs-lookup"><span data-stu-id="53921-114">To run the tool, use the Developer Command Prompt (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="53921-115">Daha fazla bilgi için bkz: [komut istemlerini](../../../docs/framework/tools/developer-command-prompt-for-vs.md). Komut isteminde aşağıdakileri yazın:</span><span class="sxs-lookup"><span data-stu-id="53921-115">For more information, see [Command Prompts](../../../docs/framework/tools/developer-command-prompt-for-vs.md).At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53921-116">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="53921-116">Syntax</span></span>  
  
```  
sqlmetal [options] [<input file>]  
```  
  
## <a name="options"></a><span data-ttu-id="53921-117">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="53921-117">Options</span></span>  
 <span data-ttu-id="53921-118">En son geçerli seçenek listesini görüntülemek için şunu yazın `sqlmetal /?` yüklü konumdan bir komut isteminde.</span><span class="sxs-lookup"><span data-stu-id="53921-118">To view the most current option list, type `sqlmetal /?` at a command prompt from the installed location.</span></span>  
  
 <span data-ttu-id="53921-119">**Bağlantı seçenekleri**</span><span class="sxs-lookup"><span data-stu-id="53921-119">**Connection Options**</span></span>  
  
|<span data-ttu-id="53921-120">Seçenek</span><span class="sxs-lookup"><span data-stu-id="53921-120">Option</span></span>|<span data-ttu-id="53921-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="53921-121">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="53921-122">**/ Server:**  *\<adı >*</span><span class="sxs-lookup"><span data-stu-id="53921-122">**/server:** *\<name>*</span></span>|<span data-ttu-id="53921-123">Veritabanı sunucusu adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="53921-123">Specifies database server name.</span></span>|  
|<span data-ttu-id="53921-124">**/ Veritabanı:**  *\<adı >*</span><span class="sxs-lookup"><span data-stu-id="53921-124">**/database:** *\<name>*</span></span>|<span data-ttu-id="53921-125">Sunucuda veritabanı kataloğu belirtir.</span><span class="sxs-lookup"><span data-stu-id="53921-125">Specifies database catalog on server.</span></span>|  
|<span data-ttu-id="53921-126">**/ User:**  *\<adı >*</span><span class="sxs-lookup"><span data-stu-id="53921-126">**/user:** *\<name>*</span></span>|<span data-ttu-id="53921-127">Oturum açma kullanıcı kimliği belirtir. Varsayılan değer: Windows kimlik doğrulaması kullan.</span><span class="sxs-lookup"><span data-stu-id="53921-127">Specifies logon user id. Default value: Use Windows authentication.</span></span>|  
|<span data-ttu-id="53921-128">**/ Password:**  *\<parolası >*</span><span class="sxs-lookup"><span data-stu-id="53921-128">**/password:** *\<password>*</span></span>|<span data-ttu-id="53921-129">Oturum açma parolasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="53921-129">Specifies logon password.</span></span> <span data-ttu-id="53921-130">Varsayılan değer: Windows kimlik doğrulaması kullan.</span><span class="sxs-lookup"><span data-stu-id="53921-130">Default value: Use Windows authentication.</span></span>|  
|<span data-ttu-id="53921-131">**/ conn:**  *\<bağlantı dizesi >*</span><span class="sxs-lookup"><span data-stu-id="53921-131">**/conn:** *\<connection string>*</span></span>|<span data-ttu-id="53921-132">Veritabanı bağlantısı dizesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="53921-132">Specifies database connection string.</span></span> <span data-ttu-id="53921-133">Kullanılamaz **/Server**, **/veritabanı**, **/user**, veya **/Password** seçenekleri.</span><span class="sxs-lookup"><span data-stu-id="53921-133">Cannot be used with **/server**, **/database**, **/user**, or **/password** options.</span></span><br /><br /> <span data-ttu-id="53921-134">Dosya adını bağlantı dizesine eklemeyin.</span><span class="sxs-lookup"><span data-stu-id="53921-134">Do not include the file name in the connection string.</span></span> <span data-ttu-id="53921-135">Bunun yerine, dosya adını giriş dosyası olarak komut satırına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="53921-135">Instead, add the file name to the command line as the input file.</span></span> <span data-ttu-id="53921-136">Örneğin, aşağıdaki satırı "c:\northwnd.mdf" Giriş dosyası belirtir: **sqlmetal /code:"c:\northwind.cs" /language:csharp "c:\northwnd.mdf"**.</span><span class="sxs-lookup"><span data-stu-id="53921-136">For example, the following line specifies "c:\northwnd.mdf" as the input file: **sqlmetal /code:"c:\northwind.cs" /language:csharp "c:\northwnd.mdf"**.</span></span>|  
|<span data-ttu-id="53921-137">**/ timeout:**  *\<saniye >*</span><span class="sxs-lookup"><span data-stu-id="53921-137">**/timeout:** *\<seconds>*</span></span>|<span data-ttu-id="53921-138">SqlMetal veritabanına eriştiğinde, zaman aşımı değerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="53921-138">Specifies time-out value when SqlMetal accesses the database.</span></span> <span data-ttu-id="53921-139">Varsayılan değer: 0 (yani, zaman sınırı yok).</span><span class="sxs-lookup"><span data-stu-id="53921-139">Default value: 0 (that is, no time limit).</span></span>|  
  
 <span data-ttu-id="53921-140">**Ayıklama seçenekleri**</span><span class="sxs-lookup"><span data-stu-id="53921-140">**Extraction options**</span></span>  
  
|<span data-ttu-id="53921-141">Seçenek</span><span class="sxs-lookup"><span data-stu-id="53921-141">Option</span></span>|<span data-ttu-id="53921-142">Açıklama</span><span class="sxs-lookup"><span data-stu-id="53921-142">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="53921-143">**/Views**</span><span class="sxs-lookup"><span data-stu-id="53921-143">**/views**</span></span>|<span data-ttu-id="53921-144">Veritabanı görünümlerini ayıklar.</span><span class="sxs-lookup"><span data-stu-id="53921-144">Extracts database views.</span></span>|  
|<span data-ttu-id="53921-145">**/Functions**</span><span class="sxs-lookup"><span data-stu-id="53921-145">**/functions**</span></span>|<span data-ttu-id="53921-146">Veritabanı işlevlerini ayıklar.</span><span class="sxs-lookup"><span data-stu-id="53921-146">Extracts database functions.</span></span>|  
|<span data-ttu-id="53921-147">**/sprocs**</span><span class="sxs-lookup"><span data-stu-id="53921-147">**/sprocs**</span></span>|<span data-ttu-id="53921-148">Saklı yordamları ayıklar.</span><span class="sxs-lookup"><span data-stu-id="53921-148">Extracts stored procedures.</span></span>|  
  
 <span data-ttu-id="53921-149">**Çıkış Seçenekleri**</span><span class="sxs-lookup"><span data-stu-id="53921-149">**Output options**</span></span>  
  
|<span data-ttu-id="53921-150">Seçenek</span><span class="sxs-lookup"><span data-stu-id="53921-150">Option</span></span>|<span data-ttu-id="53921-151">Açıklama</span><span class="sxs-lookup"><span data-stu-id="53921-151">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="53921-152">**/DBML** *[: dosyası]*</span><span class="sxs-lookup"><span data-stu-id="53921-152">**/dbml** *[:file]*</span></span>|<span data-ttu-id="53921-153">Çıkışı .dbml olarak gönderir.</span><span class="sxs-lookup"><span data-stu-id="53921-153">Sends output as .dbml.</span></span> <span data-ttu-id="53921-154">Kullanılamaz **/map** seçeneği.</span><span class="sxs-lookup"><span data-stu-id="53921-154">Cannot be used with **/map** option.</span></span>|  
|<span data-ttu-id="53921-155">**/ kod** *[: dosyası]*</span><span class="sxs-lookup"><span data-stu-id="53921-155">**/code** *[:file]*</span></span>|<span data-ttu-id="53921-156">Çıkışı kaynak kodu olarak gönderir.</span><span class="sxs-lookup"><span data-stu-id="53921-156">Sends output as source code.</span></span> <span data-ttu-id="53921-157">Kullanılamaz **/dbml** seçeneği.</span><span class="sxs-lookup"><span data-stu-id="53921-157">Cannot be used with **/dbml** option.</span></span>|  
|<span data-ttu-id="53921-158">**/ map** *[: dosyası]*</span><span class="sxs-lookup"><span data-stu-id="53921-158">**/map** *[:file]*</span></span>|<span data-ttu-id="53921-159">Öznitelikler yerine bir XML eşleme dosyası oluşturur.</span><span class="sxs-lookup"><span data-stu-id="53921-159">Generates an XML mapping file instead of attributes.</span></span> <span data-ttu-id="53921-160">Kullanılamaz **/dbml** seçeneği.</span><span class="sxs-lookup"><span data-stu-id="53921-160">Cannot be used with **/dbml** option.</span></span>|  
  
 <span data-ttu-id="53921-161">**Çeşitli**</span><span class="sxs-lookup"><span data-stu-id="53921-161">**Miscellaneous**</span></span>  
  
|<span data-ttu-id="53921-162">Seçenek</span><span class="sxs-lookup"><span data-stu-id="53921-162">Option</span></span>|<span data-ttu-id="53921-163">Açıklama</span><span class="sxs-lookup"><span data-stu-id="53921-163">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="53921-164">**/Language:**  *\<dil >*</span><span class="sxs-lookup"><span data-stu-id="53921-164">**/language:** *\<language>*</span></span>|<span data-ttu-id="53921-165">Kaynak kod dilini belirtir.</span><span class="sxs-lookup"><span data-stu-id="53921-165">Specifies source code language.</span></span><br /><br /> <span data-ttu-id="53921-166">Geçerli  *\<dil >*: vb, csharp.</span><span class="sxs-lookup"><span data-stu-id="53921-166">Valid *\<language>*: vb, csharp.</span></span><br /><br /> <span data-ttu-id="53921-167">Varsayılan değer: Kod dosyası adındaki uzantıdan türetilir.</span><span class="sxs-lookup"><span data-stu-id="53921-167">Default value: Derived from extension on code file name.</span></span>|  
|<span data-ttu-id="53921-168">**/ Namespace:**  *\<adı >*</span><span class="sxs-lookup"><span data-stu-id="53921-168">**/namespace:** *\<name>*</span></span>|<span data-ttu-id="53921-169">Üretilen kodun ad alanını belirtir.</span><span class="sxs-lookup"><span data-stu-id="53921-169">Specifies namespace of the generated code.</span></span> <span data-ttu-id="53921-170">Varsayılan değer: ad alanı yok.</span><span class="sxs-lookup"><span data-stu-id="53921-170">Default value: no namespace.</span></span>|  
|<span data-ttu-id="53921-171">**/ Context:**  *\<türü >*</span><span class="sxs-lookup"><span data-stu-id="53921-171">**/context:** *\<type>*</span></span>|<span data-ttu-id="53921-172">Veri bağlamı sınıfının adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="53921-172">Specifies name of data context class.</span></span> <span data-ttu-id="53921-173">Varsayılan değer: Veritabanı adından türetilir.</span><span class="sxs-lookup"><span data-stu-id="53921-173">Default value: Derived from database name.</span></span>|  
|<span data-ttu-id="53921-174">**/entitybase:**  *\<türü >*</span><span class="sxs-lookup"><span data-stu-id="53921-174">**/entitybase:** *\<type>*</span></span>|<span data-ttu-id="53921-175">Üretilen kodda varlık sınıflarının temel sınıfını belirtir.</span><span class="sxs-lookup"><span data-stu-id="53921-175">Specifies the base class of the entity classes in the generated code.</span></span> <span data-ttu-id="53921-176">Varsayılan değer: Varlıkların temel sınıfı yoktur.</span><span class="sxs-lookup"><span data-stu-id="53921-176">Default value: Entities have no base class.</span></span>|  
|<span data-ttu-id="53921-177">**/ Çoğul**</span><span class="sxs-lookup"><span data-stu-id="53921-177">**/pluralize**</span></span>|<span data-ttu-id="53921-178">Sınıf ve üye adlarını otomatik olarak çoğullaştırır veya tekilleştirir.</span><span class="sxs-lookup"><span data-stu-id="53921-178">Automatically pluralizes or singularizes class and member names.</span></span><br /><br /> <span data-ttu-id="53921-179">Bu seçenek yalnızca ABD'de kullanılabilir. İngilizce sürümü.</span><span class="sxs-lookup"><span data-stu-id="53921-179">This option is available only in the U.S. English version.</span></span>|  
|<span data-ttu-id="53921-180">**/Serialization:**  *\<seçeneği >*</span><span class="sxs-lookup"><span data-stu-id="53921-180">**/serialization:** *\<option>*</span></span>|<span data-ttu-id="53921-181">Seri hale getirilebilir sınıflar oluşturur.</span><span class="sxs-lookup"><span data-stu-id="53921-181">Generates serializable classes.</span></span><br /><br /> <span data-ttu-id="53921-182">Geçerli  *\<seçeneği >*: None, Unidirectional.</span><span class="sxs-lookup"><span data-stu-id="53921-182">Valid *\<option>*: None, Unidirectional.</span></span> <span data-ttu-id="53921-183">Varsayılan değer: Hiçbiri.</span><span class="sxs-lookup"><span data-stu-id="53921-183">Default value: None.</span></span><br /><br /> <span data-ttu-id="53921-184">Daha fazla bilgi için bkz: [seri hale getirme](../../../docs/framework/data/adonet/sql/linq/serialization.md).</span><span class="sxs-lookup"><span data-stu-id="53921-184">For more information, see [Serialization](../../../docs/framework/data/adonet/sql/linq/serialization.md).</span></span>|  
  
 <span data-ttu-id="53921-185">**Giriş dosyası**</span><span class="sxs-lookup"><span data-stu-id="53921-185">**Input File**</span></span>  
  
|<span data-ttu-id="53921-186">Seçenek</span><span class="sxs-lookup"><span data-stu-id="53921-186">Option</span></span>|<span data-ttu-id="53921-187">Açıklama</span><span class="sxs-lookup"><span data-stu-id="53921-187">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="53921-188">**\<Giriş dosyası >**</span><span class="sxs-lookup"><span data-stu-id="53921-188">**\<input file>**</span></span>|<span data-ttu-id="53921-189">Bir SQL Server Express .mdf dosyasını belirten bir [!INCLUDE[ssEW](../../../includes/ssew-md.md)] .sdf dosya ya da .dbml Ara dosyası.</span><span class="sxs-lookup"><span data-stu-id="53921-189">Specifies a SQL Server Express .mdf file, a [!INCLUDE[ssEW](../../../includes/ssew-md.md)] .sdf file, or a .dbml intermediate file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="53921-190">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="53921-190">Remarks</span></span>  
 <span data-ttu-id="53921-191">SqlMetal işlevi aslında iki adımdan oluşur:</span><span class="sxs-lookup"><span data-stu-id="53921-191">SqlMetal functionality actually involves two steps:</span></span>  
  
-   <span data-ttu-id="53921-192">Veritabanını meta verilerini bir .dbml dosyasına ayıklama.</span><span class="sxs-lookup"><span data-stu-id="53921-192">Extracting the metadata of the database into a .dbml file.</span></span>  
  
-   <span data-ttu-id="53921-193">Kod çıktı dosyası oluşturma.</span><span class="sxs-lookup"><span data-stu-id="53921-193">Generating a code output file.</span></span>  
  
     <span data-ttu-id="53921-194">Komut satırı seçeneklerini kullanarak, üretebilir [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] veya C# kaynak kodu veya bir XML eşleme dosyası oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="53921-194">By using the appropriate command-line options, you can produce [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] or C# source code, or you can produce an XML mapping file.</span></span>  
  
 <span data-ttu-id="53921-195">Meta verileri bir .mdf dosyasından ayıklamak için, .mdf dosyası adını tüm diğer seçeneklerden sonra belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="53921-195">To extract the metadata from an .mdf file, you must specify the name of the .mdf file after all other options.</span></span>  
  
 <span data-ttu-id="53921-196">Öyle değilse **/Server** belirtilirse, **localhost/sqlexpress** varsayılır.</span><span class="sxs-lookup"><span data-stu-id="53921-196">If no **/server** is specified, **localhost/sqlexpress** is assumed.</span></span>  
  
 [!INCLUDE[sqprsqext](../../../includes/sqprsqext-md.md)]<span data-ttu-id="53921-197">bir veya daha fazla aşağıdaki koşullar doğruysa, bir özel durum oluşturur:</span><span class="sxs-lookup"><span data-stu-id="53921-197"> throws an exception if one or more of the following conditions are true:</span></span>  
  
-   <span data-ttu-id="53921-198">SqlMetal, kendi kendini çağıran bir saklı yordam ayıklamaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="53921-198">SqlMetal tries to extract a stored procedure that calls itself.</span></span>  
  
-   <span data-ttu-id="53921-199">Bir saklı yordam, işlev veya görünümün iç içe geçme düzeyini 32'yi aşıyor.</span><span class="sxs-lookup"><span data-stu-id="53921-199">The nesting level of a stored procedure, function, or view exceeds 32.</span></span>  
  
     <span data-ttu-id="53921-200">SqlMetal, bu özel durumu yakalar ve bir uyarı olarak bildirir.</span><span class="sxs-lookup"><span data-stu-id="53921-200">SqlMetal catches this exception and reports it as a warning.</span></span>  
  
 <span data-ttu-id="53921-201">Bir giriş dosyası adı belirtmek için, adı komut satırına giriş dosyası olarak ekleyin.</span><span class="sxs-lookup"><span data-stu-id="53921-201">To specify an input file name, add the name to the command line as the input file.</span></span> <span data-ttu-id="53921-202">Dosya adı bağlantı dizesinde dahil olmak üzere (kullanarak **/conn** seçeneği) desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="53921-202">Including the file name in the connection string (using the **/conn** option) is not supported.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="53921-203">Örnekler</span><span class="sxs-lookup"><span data-stu-id="53921-203">Examples</span></span>  
 <span data-ttu-id="53921-204">Ayıklanan SQL meta verileri içeren bir .dbml dosyası oluşturun:</span><span class="sxs-lookup"><span data-stu-id="53921-204">Generate a .dbml file that includes extracted SQL metadata:</span></span>  
  
 <span data-ttu-id="53921-205">**sqlmetal /server:myserver /database:northwind /dbml:mymeta.dbml**</span><span class="sxs-lookup"><span data-stu-id="53921-205">**sqlmetal /server:myserver /database:northwind /dbml:mymeta.dbml**</span></span>  
  
 <span data-ttu-id="53921-206">SQL Server Express kullanarak bir .mdf dosyasından ayıklanan SQL meta verilerini içeren bir .dbml dosyası oluşturun:</span><span class="sxs-lookup"><span data-stu-id="53921-206">Generate a .dbml file that includes extracted SQL metadata from an .mdf file by using SQL Server Express:</span></span>  
  
 <span data-ttu-id="53921-207">**sqlmetal /dbml:mymeta.dbml mydbfile.mdf**</span><span class="sxs-lookup"><span data-stu-id="53921-207">**sqlmetal /dbml:mymeta.dbml mydbfile.mdf**</span></span>  
  
 <span data-ttu-id="53921-208">SQL Server Express'ten ayıklanan SQL meta verilerini içeren bir .dbml dosyası oluşturun:</span><span class="sxs-lookup"><span data-stu-id="53921-208">Generate a .dbml file that includes extracted SQL metadata from SQL Server Express:</span></span>  
  
 <span data-ttu-id="53921-209">**sqlmetal /server:.\sqlexpress /dbml:mymeta.dbml /database:northwind**</span><span class="sxs-lookup"><span data-stu-id="53921-209">**sqlmetal /server:.\sqlexpress /dbml:mymeta.dbml /database:northwind**</span></span>  
  
 <span data-ttu-id="53921-210">Dbml meta veri dosyasından kaynak kodu oluşturun:</span><span class="sxs-lookup"><span data-stu-id="53921-210">Generate source code from a .dbml metadata file:</span></span>  
  
 <span data-ttu-id="53921-211">**sqlmetal /namespace:nwind /code:nwind.cs /language:csharp mymetal.dbml**</span><span class="sxs-lookup"><span data-stu-id="53921-211">**sqlmetal /namespace:nwind /code:nwind.cs /language:csharp mymetal.dbml**</span></span>  
  
 <span data-ttu-id="53921-212">Doğrudan SQL meta verilerinden kaynak kodu oluşturun:</span><span class="sxs-lookup"><span data-stu-id="53921-212">Generate source code from SQL metadata directly:</span></span>  
  
 <span data-ttu-id="53921-213">**sqlmetal /server:myserver /database:northwind /namespace:nwind /code:nwind.cs /language:csharp**</span><span class="sxs-lookup"><span data-stu-id="53921-213">**sqlmetal /server:myserver /database:northwind /namespace:nwind /code:nwind.cs /language:csharp**</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="53921-214">Kullandığınızda **/ çoğul** seçeneği Northwind örnek veritabanı ile aşağıdaki davranışa dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="53921-214">When you use the **/pluralize** option with the Northwind sample database, note the following behavior.</span></span> <span data-ttu-id="53921-215">SqlMetal tablolar için satır türünde adlar oluşturduğunda, tablo adları tekildir.</span><span class="sxs-lookup"><span data-stu-id="53921-215">When SqlMetal makes row-type names for tables, the table names are singular.</span></span> <span data-ttu-id="53921-216">Ne zaman kolaylaştırır <xref:System.Data.Linq.DataContext> özellikleri tablolar için tablo adlarının çoğul.</span><span class="sxs-lookup"><span data-stu-id="53921-216">When it makes <xref:System.Data.Linq.DataContext> properties for tables, the table names are plural.</span></span> <span data-ttu-id="53921-217">Tesadüfen, Northwind örnek veritabanındaki tablolar zaten çoğuldur.</span><span class="sxs-lookup"><span data-stu-id="53921-217">Coincidentally, the tables in the Northwind sample database are already plural.</span></span> <span data-ttu-id="53921-218">Bu nedenle, bu bölümün çalıştığını görmezsiniz.</span><span class="sxs-lookup"><span data-stu-id="53921-218">Therefore, you do not see that part working.</span></span> <span data-ttu-id="53921-219">Veritabanı tablolarını tekil olarak adlandırmak ortak uygulama olsa da, toplulukları çoğul olarak adlandırmak da .NET'te ortak bir uygulamadır.</span><span class="sxs-lookup"><span data-stu-id="53921-219">Although it is common practice to name database tables singular, it is also a common practice in .NET to name collections plural.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53921-220">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="53921-220">See Also</span></span>  
 [<span data-ttu-id="53921-221">Nasıl yapılır: Visual Basic veya C# içinde nesne modeli oluşturma</span><span class="sxs-lookup"><span data-stu-id="53921-221">How to: Generate the Object Model in Visual Basic or C#</span></span>](../../../docs/framework/data/adonet/sql/linq/how-to-generate-the-object-model-in-visual-basic-or-csharp.md)  
 [<span data-ttu-id="53921-222">LINQ-SQL kod oluşturma</span><span class="sxs-lookup"><span data-stu-id="53921-222">Code Generation in LINQ to SQL</span></span>](../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)  
 [<span data-ttu-id="53921-223">Dış eşleme</span><span class="sxs-lookup"><span data-stu-id="53921-223">External Mapping</span></span>](../../../docs/framework/data/adonet/sql/linq/external-mapping.md)
