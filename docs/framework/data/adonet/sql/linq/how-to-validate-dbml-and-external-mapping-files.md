---
title: "Nasıl yapılır: DBML ve dış eşleme dosyaları doğrula"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d9ea37f5-0a9e-4401-8fc3-1e6fd44c49f9
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: c4c17b41f9bee3ce43b7627343fec2b5a69dbba8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-validate-dbml-and-external-mapping-files"></a><span data-ttu-id="9329e-102">Nasıl yapılır: DBML ve dış eşleme dosyaları doğrula</span><span class="sxs-lookup"><span data-stu-id="9329e-102">How to: Validate DBML and External Mapping Files</span></span>
<span data-ttu-id="9329e-103">Dış eşleme dosyaları ve değiştirmeniz .dbml dosyaları ilgili şema tanımlarını karşı doğrulanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9329e-103">External mapping files and .dbml files that you modify must be validated against their respective schema definitions.</span></span> <span data-ttu-id="9329e-104">Bu konuda verilmektedir [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] adımları kullanıcılarla doğrulama işlemini uygulamak için.</span><span class="sxs-lookup"><span data-stu-id="9329e-104">This topic provides [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] users with the steps to implement the validation process.</span></span>  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
### <a name="to-validate-a-dbml-or-xml-file"></a><span data-ttu-id="9329e-105">.Dbml veya XML dosyasını doğrulamak için</span><span class="sxs-lookup"><span data-stu-id="9329e-105">To validate a .dbml or XML file</span></span>  
  
1.  <span data-ttu-id="9329e-106">Visual Studio üzerinde **dosya** menüsündeki **açık**ve ardından **dosya**.</span><span class="sxs-lookup"><span data-stu-id="9329e-106">On the Visual Studio **File** menu, point to **Open**, and then click **File**.</span></span>  
  
2.  <span data-ttu-id="9329e-107">İçinde **Dosya Aç** iletişim kutusunda, .dbml veya doğrulamak istediğiniz XML eşleme dosyası'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="9329e-107">In the **Open File** dialog box, click the .dbml or XML mapping file that you want to validate.</span></span>  
  
     <span data-ttu-id="9329e-108">Dosya açılır **XML Düzenleyicisi**.</span><span class="sxs-lookup"><span data-stu-id="9329e-108">The file opens in the **XML Editor**.</span></span>  
  
3.  <span data-ttu-id="9329e-109">Pencerenin sağ tıklayın ve ardından **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="9329e-109">Right-click the window, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="9329e-110">İçinde **özellikleri** penceresinde için üç nokta düğmesine **şemaları** özelliği.</span><span class="sxs-lookup"><span data-stu-id="9329e-110">In the **Properties** window, click the ellipsis for the **Schemas** property.</span></span>  
  
     <span data-ttu-id="9329e-111">**XML şemaları** iletişim kutusu açılır.</span><span class="sxs-lookup"><span data-stu-id="9329e-111">The **XML Schemas** dialog box opens.</span></span>  
  
5.  <span data-ttu-id="9329e-112">Amacınıza uygun şema tanımı unutmayın.</span><span class="sxs-lookup"><span data-stu-id="9329e-112">Note the appropriate schema definition for your purpose.</span></span>  
  
    -   <span data-ttu-id="9329e-113">DbmlSchema.xsd .dbml dosyası doğrulanıyor şema tanımıdır.</span><span class="sxs-lookup"><span data-stu-id="9329e-113">DbmlSchema.xsd is the schema definition for validating a .dbml file.</span></span> <span data-ttu-id="9329e-114">Daha fazla bilgi için bkz: [LINQ-SQL kod oluşturma](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).</span><span class="sxs-lookup"><span data-stu-id="9329e-114">For more information, see [Code Generation in LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).</span></span>  
  
    -   <span data-ttu-id="9329e-115">LinqToSqlMapping.xsd dış XML eşleme dosyası doğrulama şema tanımı ' dir.</span><span class="sxs-lookup"><span data-stu-id="9329e-115">LinqToSqlMapping.xsd is the schema definition for validating an external XML mapping file.</span></span> <span data-ttu-id="9329e-116">Daha fazla bilgi için bkz: [dış eşleme](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="9329e-116">For more information, see [External Mapping](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md).</span></span>  
  
6.  <span data-ttu-id="9329e-117">İçinde **kullanım** istenen şema tanımı satır açılır kutusunu açın ve ardından tıklatıp sütunu **Bu şemayı kullanan**.</span><span class="sxs-lookup"><span data-stu-id="9329e-117">In the **Use** column of the desired schema definition row, click to open the drop-down box, and then click **Use this schema**.</span></span>  
  
     <span data-ttu-id="9329e-118">Şema tanımı, DBML ile ilişkili artık veya dosya eşleme XML dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="9329e-118">The schema definition file is now associated with your DBML or XML mapping file.</span></span>  
  
     <span data-ttu-id="9329e-119">Başka bir şema tanımları seçili olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="9329e-119">Make sure no other schema definitions are selected.</span></span>  
  
7.  <span data-ttu-id="9329e-120">Üzerinde **Görünüm** menüsünde tıklatın **hata listesi**.</span><span class="sxs-lookup"><span data-stu-id="9329e-120">On the **View** menu, click **Error List**.</span></span>  
  
     <span data-ttu-id="9329e-121">Hataları, uyarıları veya iletileri oluşturulmuş olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="9329e-121">Determine whether errors, warnings, or messages have been generated.</span></span> <span data-ttu-id="9329e-122">Aksi durumda, şema tanımına göre geçerli XML dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="9329e-122">If not, the XML file is valid against the schema definition.</span></span>  
  
## <a name="alternate-method-for-supplying-schema-definition"></a><span data-ttu-id="9329e-123">Şema tanımı sağlama için alternatif yöntemi</span><span class="sxs-lookup"><span data-stu-id="9329e-123">Alternate Method for Supplying Schema Definition</span></span>  
 <span data-ttu-id="9329e-124">Bazı nedenlerle uygun .xsd içinde dosya görünmüyorsa **XML şemaları** iletişim kutusu, bir Yardım konusunun .xsd dosyası indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9329e-124">If for some reason the appropriate .xsd file does not appear in the **XML Schemas** dialog box, you can download the .xsd file from a Help topic.</span></span> <span data-ttu-id="9329e-125">Aşağıdaki gerekli Unicode biçiminde indirilen dosya kaydettiğiniz yardım adımları [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] XML Düzenleyicisi.</span><span class="sxs-lookup"><span data-stu-id="9329e-125">The following steps help you save the downloaded file in the Unicode format required by the [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] XML Editor.</span></span>  
  
#### <a name="to-copy-a-schema-definition-file-from-a-help-topic"></a><span data-ttu-id="9329e-126">Bir şema tanımı dosyası bir Yardım konusunun kopyalamak için</span><span class="sxs-lookup"><span data-stu-id="9329e-126">To copy a schema definition file from a Help topic</span></span>  
  
1.  <span data-ttu-id="9329e-127">Bu konunun önceki kısımlarında açıklandığı gibi şema tanımını içerdiğinden Yardım konusunu bulun.</span><span class="sxs-lookup"><span data-stu-id="9329e-127">Locate the Help topic that contains the schema definition as described earlier in this topic.</span></span>  
  
    -   <span data-ttu-id="9329e-128">.DBML dosyalar için bkz: [LINQ-SQL kod oluşturma](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).</span><span class="sxs-lookup"><span data-stu-id="9329e-128">For .dbml files, see [Code Generation in LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).</span></span>  
  
    -   <span data-ttu-id="9329e-129">Dış eşleme dosyalar için bkz: [dış eşleme](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="9329e-129">For external mapping files, see [External Mapping](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md).</span></span>  
  
2.  <span data-ttu-id="9329e-130">Tıklatın **kod Kopyala** kod dosyası panoya kopyalamak için.</span><span class="sxs-lookup"><span data-stu-id="9329e-130">Click **Copy Code** to copy the code file to the Clipboard.</span></span>  
  
3.  <span data-ttu-id="9329e-131">Yeni bir dosya oluşturmak için Not Defteri'ni başlatın.</span><span class="sxs-lookup"><span data-stu-id="9329e-131">Start Notepad to create a new file.</span></span>  
  
4.  <span data-ttu-id="9329e-132">Panodaki kodu Not Defteri dosyaya yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="9329e-132">Paste the code from the clipboard into Notepad file.</span></span>  
  
5.  <span data-ttu-id="9329e-133">Not Defteri'ni üzerinde **dosya** menüsünde tıklatın **Kaydet**.</span><span class="sxs-lookup"><span data-stu-id="9329e-133">On the Notepad **File** menu, click **Save As**.</span></span>  
  
6.  <span data-ttu-id="9329e-134">İçinde **kodlama** kutusunda **Unicode**.</span><span class="sxs-lookup"><span data-stu-id="9329e-134">In the **Encoding** box, select **Unicode**.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="9329e-135">Bu seçim, Unicode 16 bayt sırası işaret güvence altına alır (`FFFE`) metin dosyasına eklenir.</span><span class="sxs-lookup"><span data-stu-id="9329e-135">This selection guarantees that the Unicode-16 byte-order marker (`FFFE`) is prepended to the text file.</span></span>  
  
7.  <span data-ttu-id="9329e-136">İçinde **dosya adı** kutusunda, .xsd uzantılı bir dosya adı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="9329e-136">In the **File name** box, create a file name with an .xsd extension.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9329e-137">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9329e-137">See Also</span></span>  
 [<span data-ttu-id="9329e-138">Başvuru</span><span class="sxs-lookup"><span data-stu-id="9329e-138">Reference</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)
