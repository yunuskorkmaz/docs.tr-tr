---
title: 'Nasıl yapılır: DBML ve Dış Eşleme Dosyalarını Doğrulama'
ms.date: 03/30/2017
ms.assetid: d9ea37f5-0a9e-4401-8fc3-1e6fd44c49f9
ms.openlocfilehash: b01bcf98bba185b7a4b1802f470a585371980177
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59078739"
---
# <a name="how-to-validate-dbml-and-external-mapping-files"></a><span data-ttu-id="3710d-102">Nasıl yapılır: DBML ve Dış Eşleme Dosyalarını Doğrulama</span><span class="sxs-lookup"><span data-stu-id="3710d-102">How to: Validate DBML and External Mapping Files</span></span>
<span data-ttu-id="3710d-103">Dış eşleme dosyalarını ve değişiklik .dbml dosyalarını, karşılık gelen şema tanımlarının karşı doğrulanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3710d-103">External mapping files and .dbml files that you modify must be validated against their respective schema definitions.</span></span> <span data-ttu-id="3710d-104">Bu konu, doğrulama işlemini uygulamak için Visual Studio kullanıcılarıyla adımları sağlar.</span><span class="sxs-lookup"><span data-stu-id="3710d-104">This topic provides Visual Studio users with the steps to implement the validation process.</span></span>  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
### <a name="to-validate-a-dbml-or-xml-file"></a><span data-ttu-id="3710d-105">Bir .dbml veya XML dosyasını doğrulamak için</span><span class="sxs-lookup"><span data-stu-id="3710d-105">To validate a .dbml or XML file</span></span>  
  
1.  <span data-ttu-id="3710d-106">Visual Studio'da **dosya** menüsünde **açık**ve ardından **dosya**.</span><span class="sxs-lookup"><span data-stu-id="3710d-106">On the Visual Studio **File** menu, point to **Open**, and then click **File**.</span></span>  
  
2.  <span data-ttu-id="3710d-107">İçinde **açık dosya** iletişim kutusunda, .dbml ya da doğrulamak istediğiniz XML eşleme dosyası.</span><span class="sxs-lookup"><span data-stu-id="3710d-107">In the **Open File** dialog box, click the .dbml or XML mapping file that you want to validate.</span></span>  
  
     <span data-ttu-id="3710d-108">Dosya açılır **XML Düzenleyicisi**.</span><span class="sxs-lookup"><span data-stu-id="3710d-108">The file opens in the **XML Editor**.</span></span>  
  
3.  <span data-ttu-id="3710d-109">Pencerenin sağ tıklayın ve ardından **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="3710d-109">Right-click the window, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="3710d-110">İçinde **özellikleri** penceresinde üç nokta simgesine tıklayın **şemaları** özelliği.</span><span class="sxs-lookup"><span data-stu-id="3710d-110">In the **Properties** window, click the ellipsis for the **Schemas** property.</span></span>  
  
     <span data-ttu-id="3710d-111">**XML şemaları** iletişim kutusu açılır.</span><span class="sxs-lookup"><span data-stu-id="3710d-111">The **XML Schemas** dialog box opens.</span></span>  
  
5.  <span data-ttu-id="3710d-112">Amacınıza uygun şema tanımı unutmayın.</span><span class="sxs-lookup"><span data-stu-id="3710d-112">Note the appropriate schema definition for your purpose.</span></span>  
  
    -   <span data-ttu-id="3710d-113">Bir .dbml dosyası doğrulamak için şema tanımı DbmlSchema.xsd olur.</span><span class="sxs-lookup"><span data-stu-id="3710d-113">DbmlSchema.xsd is the schema definition for validating a .dbml file.</span></span> <span data-ttu-id="3710d-114">Daha fazla bilgi için [LINQ to SQL'de kod oluşturma](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).</span><span class="sxs-lookup"><span data-stu-id="3710d-114">For more information, see [Code Generation in LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).</span></span>  
  
    -   <span data-ttu-id="3710d-115">Dış XML eşleme dosyası doğrulamak için şema tanımı LinqToSqlMapping.xsd olur.</span><span class="sxs-lookup"><span data-stu-id="3710d-115">LinqToSqlMapping.xsd is the schema definition for validating an external XML mapping file.</span></span> <span data-ttu-id="3710d-116">Daha fazla bilgi için [dış eşleme](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="3710d-116">For more information, see [External Mapping](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md).</span></span>  
  
6.  <span data-ttu-id="3710d-117">İçinde **kullanım** açılır kutusunu açın ve ardından tıklatıp istediğiniz şema tanımı satırın sütun **Bu şemayı kullan**.</span><span class="sxs-lookup"><span data-stu-id="3710d-117">In the **Use** column of the desired schema definition row, click to open the drop-down box, and then click **Use this schema**.</span></span>  
  
     <span data-ttu-id="3710d-118">Şema tanımı, DBML ile ilişkili şimdi veya eşleme dosyası XML dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="3710d-118">The schema definition file is now associated with your DBML or XML mapping file.</span></span>  
  
     <span data-ttu-id="3710d-119">Başka bir şema tanımları seçili olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="3710d-119">Make sure no other schema definitions are selected.</span></span>  
  
7.  <span data-ttu-id="3710d-120">Üzerinde **görünümü** menüsünü tıklatın **hata listesi**.</span><span class="sxs-lookup"><span data-stu-id="3710d-120">On the **View** menu, click **Error List**.</span></span>  
  
     <span data-ttu-id="3710d-121">Hataları, uyarıları ve iletileri oluşturulmuş olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="3710d-121">Determine whether errors, warnings, or messages have been generated.</span></span> <span data-ttu-id="3710d-122">Aksi durumda, şema tanımıyla geçerli XML dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="3710d-122">If not, the XML file is valid against the schema definition.</span></span>  
  
## <a name="alternate-method-for-supplying-schema-definition"></a><span data-ttu-id="3710d-123">Şema tanımı sağlama için alternatif yöntem</span><span class="sxs-lookup"><span data-stu-id="3710d-123">Alternate Method for Supplying Schema Definition</span></span>  
 <span data-ttu-id="3710d-124">Herhangi bir nedenle uygun .xsd içinde dosya görünmüyorsa **XML şemaları** iletişim kutusu, bir Yardım konusunun .xsd dosyasını indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3710d-124">If for some reason the appropriate .xsd file does not appear in the **XML Schemas** dialog box, you can download the .xsd file from a Help topic.</span></span> <span data-ttu-id="3710d-125">Aşağıdaki adımlar indirilen dosyayı Visual Studio XML Düzenleyicisi tarafından gerekli Unicode biçiminde kaydedin yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="3710d-125">The following steps help you save the downloaded file in the Unicode format required by the Visual Studio XML Editor.</span></span>  
  
#### <a name="to-copy-a-schema-definition-file-from-a-help-topic"></a><span data-ttu-id="3710d-126">Bir Yardım konusunun bir şema tanımı dosyasını kopyalamak için</span><span class="sxs-lookup"><span data-stu-id="3710d-126">To copy a schema definition file from a Help topic</span></span>  
  
1.  <span data-ttu-id="3710d-127">Bu konunun önceki kısımlarında açıklandığı gibi şema tanımını içerdiğinden Yardım konusu bulun.</span><span class="sxs-lookup"><span data-stu-id="3710d-127">Locate the Help topic that contains the schema definition as described earlier in this topic.</span></span>  
  
    -   <span data-ttu-id="3710d-128">.DBML dosyalar için bkz: [LINQ to SQL'de kod oluşturma](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).</span><span class="sxs-lookup"><span data-stu-id="3710d-128">For .dbml files, see [Code Generation in LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).</span></span>  
  
    -   <span data-ttu-id="3710d-129">Dış eşleme dosyaları için bkz: [dış eşleme](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="3710d-129">For external mapping files, see [External Mapping](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md).</span></span>  
  
2.  <span data-ttu-id="3710d-130">Tıklayın **kopyalama kod** kod dosyası panoya kopyalamak için.</span><span class="sxs-lookup"><span data-stu-id="3710d-130">Click **Copy Code** to copy the code file to the Clipboard.</span></span>  
  
3.  <span data-ttu-id="3710d-131">Yeni bir dosya oluşturmak için Not Defteri'ni başlatın.</span><span class="sxs-lookup"><span data-stu-id="3710d-131">Start Notepad to create a new file.</span></span>  
  
4.  <span data-ttu-id="3710d-132">Pano koddan not defteri dosyasına yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="3710d-132">Paste the code from the clipboard into Notepad file.</span></span>  
  
5.  <span data-ttu-id="3710d-133">Not Defteri'ni üzerinde **dosya** menüsünde tıklayın **Kaydet**.</span><span class="sxs-lookup"><span data-stu-id="3710d-133">On the Notepad **File** menu, click **Save As**.</span></span>  
  
6.  <span data-ttu-id="3710d-134">İçinde **kodlama** kutusunda **Unicode**.</span><span class="sxs-lookup"><span data-stu-id="3710d-134">In the **Encoding** box, select **Unicode**.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="3710d-135">Bu seçim, 16 Unicode bayt sırası işareti garanti eder (`FFFE`) metin dosyasına eklenir.</span><span class="sxs-lookup"><span data-stu-id="3710d-135">This selection guarantees that the Unicode-16 byte-order marker (`FFFE`) is prepended to the text file.</span></span>  
  
7.  <span data-ttu-id="3710d-136">İçinde **dosya adı** kutusunda, bir .xsd uzantısı ile adlı bir dosya oluşturun.</span><span class="sxs-lookup"><span data-stu-id="3710d-136">In the **File name** box, create a file name with an .xsd extension.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3710d-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3710d-137">See also</span></span>

- [<span data-ttu-id="3710d-138">Başvuru</span><span class="sxs-lookup"><span data-stu-id="3710d-138">Reference</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)
