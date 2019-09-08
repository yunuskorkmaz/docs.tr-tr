---
title: 'Nasıl yapılır: DBML ve Dış Eşleme Dosyalarını Doğrulama'
ms.date: 03/30/2017
ms.assetid: d9ea37f5-0a9e-4401-8fc3-1e6fd44c49f9
ms.openlocfilehash: b5901705ac7c0692025ff1f4a4b78f976d62176d
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793045"
---
# <a name="how-to-validate-dbml-and-external-mapping-files"></a><span data-ttu-id="962c3-102">Nasıl yapılır: DBML ve Dış Eşleme Dosyalarını Doğrulama</span><span class="sxs-lookup"><span data-stu-id="962c3-102">How to: Validate DBML and External Mapping Files</span></span>

<span data-ttu-id="962c3-103">Değiştirdiğiniz dış eşleme dosyaları ve. dbml dosyaları kendi şema tanımlarına göre doğrulanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="962c3-103">External mapping files and .dbml files that you modify must be validated against their respective schema definitions.</span></span> <span data-ttu-id="962c3-104">Bu konu, Visual Studio kullanıcılarına doğrulama işlemini uygulamak için gereken adımları sağlar.</span><span class="sxs-lookup"><span data-stu-id="962c3-104">This topic provides Visual Studio users with the steps to implement the validation process.</span></span>

[!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]

### <a name="to-validate-a-dbml-or-xml-file"></a><span data-ttu-id="962c3-105">Bir. dbml veya XML dosyasını doğrulamak için</span><span class="sxs-lookup"><span data-stu-id="962c3-105">To validate a .dbml or XML file</span></span>

1. <span data-ttu-id="962c3-106">Visual Studio **Dosya** menüsünde **Aç**' ın üzerine gelin ve ardından **Dosya**' ya tıklayın.</span><span class="sxs-lookup"><span data-stu-id="962c3-106">On the Visual Studio **File** menu, point to **Open**, and then click **File**.</span></span>

2. <span data-ttu-id="962c3-107">**Dosya Aç** iletişim kutusunda, doğrulamak istediğiniz. dbml veya XML eşleme dosyasına tıklayın.</span><span class="sxs-lookup"><span data-stu-id="962c3-107">In the **Open File** dialog box, click the .dbml or XML mapping file that you want to validate.</span></span>

    <span data-ttu-id="962c3-108">Dosya **XML düzenleyicisinde**açılır.</span><span class="sxs-lookup"><span data-stu-id="962c3-108">The file opens in the **XML Editor**.</span></span>

3. <span data-ttu-id="962c3-109">Pencereye sağ tıklayın ve ardından **Özellikler**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="962c3-109">Right-click the window, and then click **Properties**.</span></span>

4. <span data-ttu-id="962c3-110">**Özellikler** penceresinde, **şemalar** özelliğinin üç nokta simgesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="962c3-110">In the **Properties** window, click the ellipsis for the **Schemas** property.</span></span>

    <span data-ttu-id="962c3-111">**XML şemaları** iletişim kutusu açılır.</span><span class="sxs-lookup"><span data-stu-id="962c3-111">The **XML Schemas** dialog box opens.</span></span>

5. <span data-ttu-id="962c3-112">Amacınıza uygun şema tanımını göz önünde edin.</span><span class="sxs-lookup"><span data-stu-id="962c3-112">Note the appropriate schema definition for your purpose.</span></span>

    - <span data-ttu-id="962c3-113">DbmlSchema. xsd, bir. dbml dosyasını doğrulamaya yönelik şema tanımıdır.</span><span class="sxs-lookup"><span data-stu-id="962c3-113">DbmlSchema.xsd is the schema definition for validating a .dbml file.</span></span> <span data-ttu-id="962c3-114">Daha fazla bilgi için bkz. [LINQ to SQL kod oluşturma](code-generation-in-linq-to-sql.md).</span><span class="sxs-lookup"><span data-stu-id="962c3-114">For more information, see [Code Generation in LINQ to SQL](code-generation-in-linq-to-sql.md).</span></span>

    - <span data-ttu-id="962c3-115">LinqToSqlMapping. xsd, bir dış XML eşleme dosyasını doğrulamaya yönelik şema tanımıdır.</span><span class="sxs-lookup"><span data-stu-id="962c3-115">LinqToSqlMapping.xsd is the schema definition for validating an external XML mapping file.</span></span> <span data-ttu-id="962c3-116">Daha fazla bilgi için bkz. [dış eşleme](external-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="962c3-116">For more information, see [External Mapping](external-mapping.md).</span></span>

6. <span data-ttu-id="962c3-117">İstenen şema tanımı satırının **kullan** sütununda, açılan kutuyu açmak için tıklayın ve ardından **Bu şemayı kullan**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="962c3-117">In the **Use** column of the desired schema definition row, click to open the drop-down box, and then click **Use this schema**.</span></span>

    <span data-ttu-id="962c3-118">Şema tanımı dosyası artık DBML veya XML eşleme dosyası ile ilişkilendirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="962c3-118">The schema definition file is now associated with your DBML or XML mapping file.</span></span>

    <span data-ttu-id="962c3-119">Başka şema tanımlarının seçili olmadığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="962c3-119">Make sure no other schema definitions are selected.</span></span>

7. <span data-ttu-id="962c3-120">**Görünüm** menüsünde **hata listesi**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="962c3-120">On the **View** menu, click **Error List**.</span></span>

    <span data-ttu-id="962c3-121">Hataların, uyarıların veya mesajların oluşturulup oluşturulmayacağını belirleme.</span><span class="sxs-lookup"><span data-stu-id="962c3-121">Determine whether errors, warnings, or messages have been generated.</span></span> <span data-ttu-id="962c3-122">Aksi takdirde, XML dosyası şema tanımına göre geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="962c3-122">If not, the XML file is valid against the schema definition.</span></span>

## <a name="alternate-method-for-supplying-schema-definition"></a><span data-ttu-id="962c3-123">Şema tanımı sağlamak için alternatif Yöntem</span><span class="sxs-lookup"><span data-stu-id="962c3-123">Alternate Method for Supplying Schema Definition</span></span>

<span data-ttu-id="962c3-124">Bazı nedenlerle uygun. xsd dosyası **XML şemaları** iletişim kutusunda görünmüyorsa, Yardım konusundan. xsd dosyasını indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="962c3-124">If for some reason the appropriate .xsd file does not appear in the **XML Schemas** dialog box, you can download the .xsd file from a Help topic.</span></span> <span data-ttu-id="962c3-125">Aşağıdaki adımlar, indirilen dosyayı Visual Studio XML Düzenleyicisi için gereken Unicode biçiminde kaydetmenize yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="962c3-125">The following steps help you save the downloaded file in the Unicode format required by the Visual Studio XML Editor.</span></span>

#### <a name="to-copy-a-schema-definition-file-from-a-help-topic"></a><span data-ttu-id="962c3-126">Yardım konusundan bir şema tanım dosyasını kopyalamak için</span><span class="sxs-lookup"><span data-stu-id="962c3-126">To copy a schema definition file from a Help topic</span></span>

1. <span data-ttu-id="962c3-127">Şema tanımını içeren yardım konusunu bu konunun önceki kısımlarında açıklandığı gibi bulun.</span><span class="sxs-lookup"><span data-stu-id="962c3-127">Locate the Help topic that contains the schema definition as described earlier in this topic.</span></span>

    - <span data-ttu-id="962c3-128">. Dbml dosyaları için bkz. [LINQ to SQL kod oluşturma](code-generation-in-linq-to-sql.md).</span><span class="sxs-lookup"><span data-stu-id="962c3-128">For .dbml files, see [Code Generation in LINQ to SQL](code-generation-in-linq-to-sql.md).</span></span>

    - <span data-ttu-id="962c3-129">Dış eşleme dosyaları için bkz. [dış eşleme](external-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="962c3-129">For external mapping files, see [External Mapping](external-mapping.md).</span></span>

2. <span data-ttu-id="962c3-130">Kod dosyasını panoya kopyalamak için **kodu kopyala** ' ya tıklayın.</span><span class="sxs-lookup"><span data-stu-id="962c3-130">Click **Copy Code** to copy the code file to the Clipboard.</span></span>

3. <span data-ttu-id="962c3-131">Yeni bir dosya oluşturmak için Not defteri 'Ni başlatın.</span><span class="sxs-lookup"><span data-stu-id="962c3-131">Start Notepad to create a new file.</span></span>

4. <span data-ttu-id="962c3-132">Panodaki kodu Notepad dosyasına yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="962c3-132">Paste the code from the clipboard into Notepad file.</span></span>

5. <span data-ttu-id="962c3-133">Not defteri **dosyası** menüsünde **farklı kaydet**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="962c3-133">On the Notepad **File** menu, click **Save As**.</span></span>

6. <span data-ttu-id="962c3-134">**Kodlama** kutusunda **Unicode**' u seçin.</span><span class="sxs-lookup"><span data-stu-id="962c3-134">In the **Encoding** box, select **Unicode**.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="962c3-135">Bu seçim, Unicode-16 bayt sıra işaretçisinin (`FFFE`) metin dosyasına eklenmiş olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="962c3-135">This selection guarantees that the Unicode-16 byte-order marker (`FFFE`) is prepended to the text file.</span></span>

7. <span data-ttu-id="962c3-136">**Dosya adı** kutusunda. xsd uzantılı bir dosya adı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="962c3-136">In the **File name** box, create a file name with an .xsd extension.</span></span>

## <a name="see-also"></a><span data-ttu-id="962c3-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="962c3-137">See also</span></span>

- [<span data-ttu-id="962c3-138">Başvuru</span><span class="sxs-lookup"><span data-stu-id="962c3-138">Reference</span></span>](reference.md)
