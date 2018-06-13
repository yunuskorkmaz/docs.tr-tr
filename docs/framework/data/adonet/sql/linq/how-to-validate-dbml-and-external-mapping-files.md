---
title: 'Nasıl yapılır: DBML ve dış eşleme dosyaları doğrula'
ms.date: 03/30/2017
ms.assetid: d9ea37f5-0a9e-4401-8fc3-1e6fd44c49f9
ms.openlocfilehash: 9bf21353aebd0ae57c51b2ddf3b31b5e7f1ac615
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33362168"
---
# <a name="how-to-validate-dbml-and-external-mapping-files"></a><span data-ttu-id="70866-102">Nasıl yapılır: DBML ve dış eşleme dosyaları doğrula</span><span class="sxs-lookup"><span data-stu-id="70866-102">How to: Validate DBML and External Mapping Files</span></span>
<span data-ttu-id="70866-103">Dış eşleme dosyaları ve değiştirmeniz .dbml dosyaları ilgili şema tanımlarını karşı doğrulanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="70866-103">External mapping files and .dbml files that you modify must be validated against their respective schema definitions.</span></span> <span data-ttu-id="70866-104">Bu konu, doğrulama işlemini uygulamak için Visual Studio kullanıcılarla adımları sağlar.</span><span class="sxs-lookup"><span data-stu-id="70866-104">This topic provides Visual Studio users with the steps to implement the validation process.</span></span>  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
### <a name="to-validate-a-dbml-or-xml-file"></a><span data-ttu-id="70866-105">.Dbml veya XML dosyasını doğrulamak için</span><span class="sxs-lookup"><span data-stu-id="70866-105">To validate a .dbml or XML file</span></span>  
  
1.  <span data-ttu-id="70866-106">Visual Studio üzerinde **dosya** menüsündeki **açık**ve ardından **dosya**.</span><span class="sxs-lookup"><span data-stu-id="70866-106">On the Visual Studio **File** menu, point to **Open**, and then click **File**.</span></span>  
  
2.  <span data-ttu-id="70866-107">İçinde **Dosya Aç** iletişim kutusunda, .dbml veya doğrulamak istediğiniz XML eşleme dosyası'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="70866-107">In the **Open File** dialog box, click the .dbml or XML mapping file that you want to validate.</span></span>  
  
     <span data-ttu-id="70866-108">Dosya açılır **XML Düzenleyicisi**.</span><span class="sxs-lookup"><span data-stu-id="70866-108">The file opens in the **XML Editor**.</span></span>  
  
3.  <span data-ttu-id="70866-109">Pencerenin sağ tıklayın ve ardından **özellikleri**.</span><span class="sxs-lookup"><span data-stu-id="70866-109">Right-click the window, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="70866-110">İçinde **özellikleri** penceresinde için üç nokta düğmesine **şemaları** özelliği.</span><span class="sxs-lookup"><span data-stu-id="70866-110">In the **Properties** window, click the ellipsis for the **Schemas** property.</span></span>  
  
     <span data-ttu-id="70866-111">**XML şemaları** iletişim kutusu açılır.</span><span class="sxs-lookup"><span data-stu-id="70866-111">The **XML Schemas** dialog box opens.</span></span>  
  
5.  <span data-ttu-id="70866-112">Amacınıza uygun şema tanımı unutmayın.</span><span class="sxs-lookup"><span data-stu-id="70866-112">Note the appropriate schema definition for your purpose.</span></span>  
  
    -   <span data-ttu-id="70866-113">DbmlSchema.xsd .dbml dosyası doğrulanıyor şema tanımıdır.</span><span class="sxs-lookup"><span data-stu-id="70866-113">DbmlSchema.xsd is the schema definition for validating a .dbml file.</span></span> <span data-ttu-id="70866-114">Daha fazla bilgi için bkz: [LINQ-SQL kod oluşturma](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).</span><span class="sxs-lookup"><span data-stu-id="70866-114">For more information, see [Code Generation in LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).</span></span>  
  
    -   <span data-ttu-id="70866-115">LinqToSqlMapping.xsd dış XML eşleme dosyası doğrulama şema tanımı ' dir.</span><span class="sxs-lookup"><span data-stu-id="70866-115">LinqToSqlMapping.xsd is the schema definition for validating an external XML mapping file.</span></span> <span data-ttu-id="70866-116">Daha fazla bilgi için bkz: [dış eşleme](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="70866-116">For more information, see [External Mapping](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md).</span></span>  
  
6.  <span data-ttu-id="70866-117">İçinde **kullanım** istenen şema tanımı satır açılır kutusunu açın ve ardından tıklatıp sütunu **Bu şemayı kullanan**.</span><span class="sxs-lookup"><span data-stu-id="70866-117">In the **Use** column of the desired schema definition row, click to open the drop-down box, and then click **Use this schema**.</span></span>  
  
     <span data-ttu-id="70866-118">Şema tanımı, DBML ile ilişkili artık veya dosya eşleme XML dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="70866-118">The schema definition file is now associated with your DBML or XML mapping file.</span></span>  
  
     <span data-ttu-id="70866-119">Başka bir şema tanımları seçili olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="70866-119">Make sure no other schema definitions are selected.</span></span>  
  
7.  <span data-ttu-id="70866-120">Üzerinde **Görünüm** menüsünde tıklatın **hata listesi**.</span><span class="sxs-lookup"><span data-stu-id="70866-120">On the **View** menu, click **Error List**.</span></span>  
  
     <span data-ttu-id="70866-121">Hataları, uyarıları veya iletileri oluşturulmuş olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="70866-121">Determine whether errors, warnings, or messages have been generated.</span></span> <span data-ttu-id="70866-122">Aksi durumda, şema tanımına göre geçerli XML dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="70866-122">If not, the XML file is valid against the schema definition.</span></span>  
  
## <a name="alternate-method-for-supplying-schema-definition"></a><span data-ttu-id="70866-123">Şema tanımı sağlama için alternatif yöntemi</span><span class="sxs-lookup"><span data-stu-id="70866-123">Alternate Method for Supplying Schema Definition</span></span>  
 <span data-ttu-id="70866-124">Bazı nedenlerle uygun .xsd içinde dosya görünmüyorsa **XML şemaları** iletişim kutusu, bir Yardım konusunun .xsd dosyası indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="70866-124">If for some reason the appropriate .xsd file does not appear in the **XML Schemas** dialog box, you can download the .xsd file from a Help topic.</span></span> <span data-ttu-id="70866-125">Aşağıdaki adımlar, Visual Studio XML Düzenleyicisi tarafından gerekli Unicode biçiminde indirilen dosya kaydetmenize yardımcı.</span><span class="sxs-lookup"><span data-stu-id="70866-125">The following steps help you save the downloaded file in the Unicode format required by the Visual Studio XML Editor.</span></span>  
  
#### <a name="to-copy-a-schema-definition-file-from-a-help-topic"></a><span data-ttu-id="70866-126">Bir şema tanımı dosyası bir Yardım konusunun kopyalamak için</span><span class="sxs-lookup"><span data-stu-id="70866-126">To copy a schema definition file from a Help topic</span></span>  
  
1.  <span data-ttu-id="70866-127">Bu konunun önceki kısımlarında açıklandığı gibi şema tanımını içerdiğinden Yardım konusunu bulun.</span><span class="sxs-lookup"><span data-stu-id="70866-127">Locate the Help topic that contains the schema definition as described earlier in this topic.</span></span>  
  
    -   <span data-ttu-id="70866-128">.DBML dosyalar için bkz: [LINQ-SQL kod oluşturma](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).</span><span class="sxs-lookup"><span data-stu-id="70866-128">For .dbml files, see [Code Generation in LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).</span></span>  
  
    -   <span data-ttu-id="70866-129">Dış eşleme dosyalar için bkz: [dış eşleme](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="70866-129">For external mapping files, see [External Mapping](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md).</span></span>  
  
2.  <span data-ttu-id="70866-130">Tıklatın **kod Kopyala** kod dosyası panoya kopyalamak için.</span><span class="sxs-lookup"><span data-stu-id="70866-130">Click **Copy Code** to copy the code file to the Clipboard.</span></span>  
  
3.  <span data-ttu-id="70866-131">Yeni bir dosya oluşturmak için Not Defteri'ni başlatın.</span><span class="sxs-lookup"><span data-stu-id="70866-131">Start Notepad to create a new file.</span></span>  
  
4.  <span data-ttu-id="70866-132">Panodaki kodu Not Defteri dosyaya yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="70866-132">Paste the code from the clipboard into Notepad file.</span></span>  
  
5.  <span data-ttu-id="70866-133">Not Defteri'ni üzerinde **dosya** menüsünde tıklatın **Kaydet**.</span><span class="sxs-lookup"><span data-stu-id="70866-133">On the Notepad **File** menu, click **Save As**.</span></span>  
  
6.  <span data-ttu-id="70866-134">İçinde **kodlama** kutusunda **Unicode**.</span><span class="sxs-lookup"><span data-stu-id="70866-134">In the **Encoding** box, select **Unicode**.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="70866-135">Bu seçim, Unicode 16 bayt sırası işaret güvence altına alır (`FFFE`) metin dosyasına eklenir.</span><span class="sxs-lookup"><span data-stu-id="70866-135">This selection guarantees that the Unicode-16 byte-order marker (`FFFE`) is prepended to the text file.</span></span>  
  
7.  <span data-ttu-id="70866-136">İçinde **dosya adı** kutusunda, .xsd uzantılı bir dosya adı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="70866-136">In the **File name** box, create a file name with an .xsd extension.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70866-137">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="70866-137">See Also</span></span>  
 [<span data-ttu-id="70866-138">Başvuru</span><span class="sxs-lookup"><span data-stu-id="70866-138">Reference</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)
