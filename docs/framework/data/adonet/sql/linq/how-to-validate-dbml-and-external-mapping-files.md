---
description: 'Daha fazla bilgi edinin: nasıl yapılır: DBML ve dış eşleme dosyalarını doğrulama'
title: 'Nasıl yapılır: DBML ve Dış Eşleme Dosyalarını Doğrulama'
ms.date: 03/30/2017
ms.assetid: d9ea37f5-0a9e-4401-8fc3-1e6fd44c49f9
ms.openlocfilehash: 46e5c787bef8e152020fc97631ef8c1c4928fe74
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785789"
---
# <a name="how-to-validate-dbml-and-external-mapping-files"></a><span data-ttu-id="23c6a-103">Nasıl yapılır: DBML ve Dış Eşleme Dosyalarını Doğrulama</span><span class="sxs-lookup"><span data-stu-id="23c6a-103">How to: Validate DBML and External Mapping Files</span></span>

<span data-ttu-id="23c6a-104">Değiştirdiğiniz dış eşleme dosyaları ve. dbml dosyaları kendi şema tanımlarına göre doğrulanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="23c6a-104">External mapping files and .dbml files that you modify must be validated against their respective schema definitions.</span></span> <span data-ttu-id="23c6a-105">Bu konu, Visual Studio kullanıcılarına doğrulama işlemini uygulamak için gereken adımları sağlar.</span><span class="sxs-lookup"><span data-stu-id="23c6a-105">This topic provides Visual Studio users with the steps to implement the validation process.</span></span>

[!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]

### <a name="to-validate-a-dbml-or-xml-file"></a><span data-ttu-id="23c6a-106">Bir. dbml veya XML dosyasını doğrulamak için</span><span class="sxs-lookup"><span data-stu-id="23c6a-106">To validate a .dbml or XML file</span></span>

1. <span data-ttu-id="23c6a-107">Visual Studio **Dosya** menüsünde **Aç**' ın üzerine gelin ve ardından **Dosya**' ya tıklayın.</span><span class="sxs-lookup"><span data-stu-id="23c6a-107">On the Visual Studio **File** menu, point to **Open**, and then click **File**.</span></span>

2. <span data-ttu-id="23c6a-108">**Dosya Aç** iletişim kutusunda, doğrulamak istediğiniz. dbml veya XML eşleme dosyasına tıklayın.</span><span class="sxs-lookup"><span data-stu-id="23c6a-108">In the **Open File** dialog box, click the .dbml or XML mapping file that you want to validate.</span></span>

    <span data-ttu-id="23c6a-109">Dosya **XML düzenleyicisinde** açılır.</span><span class="sxs-lookup"><span data-stu-id="23c6a-109">The file opens in the **XML Editor**.</span></span>

3. <span data-ttu-id="23c6a-110">Pencereye sağ tıklayın ve ardından **Özellikler**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="23c6a-110">Right-click the window, and then click **Properties**.</span></span>

4. <span data-ttu-id="23c6a-111">**Özellikler** penceresinde, **şemalar** özelliğinin üç nokta simgesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="23c6a-111">In the **Properties** window, click the ellipsis for the **Schemas** property.</span></span>

    <span data-ttu-id="23c6a-112">**XML şemaları** iletişim kutusu açılır.</span><span class="sxs-lookup"><span data-stu-id="23c6a-112">The **XML Schemas** dialog box opens.</span></span>

5. <span data-ttu-id="23c6a-113">Amacınıza uygun şema tanımını göz önünde edin.</span><span class="sxs-lookup"><span data-stu-id="23c6a-113">Note the appropriate schema definition for your purpose.</span></span>

    - <span data-ttu-id="23c6a-114">DbmlSchema. xsd, bir. dbml dosyasını doğrulamaya yönelik şema tanımıdır.</span><span class="sxs-lookup"><span data-stu-id="23c6a-114">DbmlSchema.xsd is the schema definition for validating a .dbml file.</span></span> <span data-ttu-id="23c6a-115">Daha fazla bilgi için bkz. [LINQ to SQL kod oluşturma](code-generation-in-linq-to-sql.md).</span><span class="sxs-lookup"><span data-stu-id="23c6a-115">For more information, see [Code Generation in LINQ to SQL](code-generation-in-linq-to-sql.md).</span></span>

    - <span data-ttu-id="23c6a-116">LinqToSqlMapping. xsd, bir dış XML eşleme dosyasını doğrulamaya yönelik şema tanımıdır.</span><span class="sxs-lookup"><span data-stu-id="23c6a-116">LinqToSqlMapping.xsd is the schema definition for validating an external XML mapping file.</span></span> <span data-ttu-id="23c6a-117">Daha fazla bilgi için bkz. [dış eşleme](external-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="23c6a-117">For more information, see [External Mapping](external-mapping.md).</span></span>

6. <span data-ttu-id="23c6a-118">İstenen şema tanımı satırının **kullan** sütununda, açılan kutuyu açmak için tıklayın ve ardından **Bu şemayı kullan**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="23c6a-118">In the **Use** column of the desired schema definition row, click to open the drop-down box, and then click **Use this schema**.</span></span>

    <span data-ttu-id="23c6a-119">Şema tanımı dosyası artık DBML veya XML eşleme dosyası ile ilişkilendirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="23c6a-119">The schema definition file is now associated with your DBML or XML mapping file.</span></span>

    <span data-ttu-id="23c6a-120">Başka şema tanımlarının seçili olmadığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="23c6a-120">Make sure no other schema definitions are selected.</span></span>

7. <span data-ttu-id="23c6a-121">**Görünüm** menüsünde **hata listesi**' a tıklayın.</span><span class="sxs-lookup"><span data-stu-id="23c6a-121">On the **View** menu, click **Error List**.</span></span>

    <span data-ttu-id="23c6a-122">Hataların, uyarıların veya mesajların oluşturulup oluşturulmayacağını belirleme.</span><span class="sxs-lookup"><span data-stu-id="23c6a-122">Determine whether errors, warnings, or messages have been generated.</span></span> <span data-ttu-id="23c6a-123">Aksi takdirde, XML dosyası şema tanımına göre geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="23c6a-123">If not, the XML file is valid against the schema definition.</span></span>

## <a name="alternate-method-for-supplying-schema-definition"></a><span data-ttu-id="23c6a-124">Şema tanımı sağlamak için alternatif Yöntem</span><span class="sxs-lookup"><span data-stu-id="23c6a-124">Alternate Method for Supplying Schema Definition</span></span>

<span data-ttu-id="23c6a-125">Bazı nedenlerle uygun. xsd dosyası **XML şemaları** iletişim kutusunda görünmüyorsa, Yardım konusundan. xsd dosyasını indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="23c6a-125">If for some reason the appropriate .xsd file does not appear in the **XML Schemas** dialog box, you can download the .xsd file from a Help topic.</span></span> <span data-ttu-id="23c6a-126">Aşağıdaki adımlar, indirilen dosyayı Visual Studio XML Düzenleyicisi için gereken Unicode biçiminde kaydetmenize yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="23c6a-126">The following steps help you save the downloaded file in the Unicode format required by the Visual Studio XML Editor.</span></span>

#### <a name="to-copy-a-schema-definition-file-from-a-help-topic"></a><span data-ttu-id="23c6a-127">Yardım konusundan bir şema tanım dosyasını kopyalamak için</span><span class="sxs-lookup"><span data-stu-id="23c6a-127">To copy a schema definition file from a Help topic</span></span>

1. <span data-ttu-id="23c6a-128">Şema tanımını içeren yardım konusunu bu konunun önceki kısımlarında açıklandığı gibi bulun.</span><span class="sxs-lookup"><span data-stu-id="23c6a-128">Locate the Help topic that contains the schema definition as described earlier in this topic.</span></span>

    - <span data-ttu-id="23c6a-129">. Dbml dosyaları için bkz. [LINQ to SQL kod oluşturma](code-generation-in-linq-to-sql.md).</span><span class="sxs-lookup"><span data-stu-id="23c6a-129">For .dbml files, see [Code Generation in LINQ to SQL](code-generation-in-linq-to-sql.md).</span></span>

    - <span data-ttu-id="23c6a-130">Dış eşleme dosyaları için bkz. [dış eşleme](external-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="23c6a-130">For external mapping files, see [External Mapping](external-mapping.md).</span></span>

2. <span data-ttu-id="23c6a-131">Kod dosyasını panoya kopyalamak için **kodu kopyala** ' ya tıklayın.</span><span class="sxs-lookup"><span data-stu-id="23c6a-131">Click **Copy Code** to copy the code file to the Clipboard.</span></span>

3. <span data-ttu-id="23c6a-132">Yeni bir dosya oluşturmak için Not defteri 'Ni başlatın.</span><span class="sxs-lookup"><span data-stu-id="23c6a-132">Start Notepad to create a new file.</span></span>

4. <span data-ttu-id="23c6a-133">Panodaki kodu Notepad dosyasına yapıştırın.</span><span class="sxs-lookup"><span data-stu-id="23c6a-133">Paste the code from the clipboard into Notepad file.</span></span>

5. <span data-ttu-id="23c6a-134">Not defteri **dosyası** menüsünde **farklı kaydet**' e tıklayın.</span><span class="sxs-lookup"><span data-stu-id="23c6a-134">On the Notepad **File** menu, click **Save As**.</span></span>

6. <span data-ttu-id="23c6a-135">**Kodlama** kutusunda **Unicode**' u seçin.</span><span class="sxs-lookup"><span data-stu-id="23c6a-135">In the **Encoding** box, select **Unicode**.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="23c6a-136">Bu seçim, Unicode-16 bayt sıra işaretçisinin ( `FFFE` ) metin dosyasına eklenmiş olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="23c6a-136">This selection guarantees that the Unicode-16 byte-order marker (`FFFE`) is prepended to the text file.</span></span>

7. <span data-ttu-id="23c6a-137">**Dosya adı** kutusunda. xsd uzantılı bir dosya adı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="23c6a-137">In the **File name** box, create a file name with an .xsd extension.</span></span>

## <a name="see-also"></a><span data-ttu-id="23c6a-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="23c6a-138">See also</span></span>

- [<span data-ttu-id="23c6a-139">Başvuru</span><span class="sxs-lookup"><span data-stu-id="23c6a-139">Reference</span></span>](reference.md)
