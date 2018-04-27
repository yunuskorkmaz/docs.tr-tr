---
title: XML ile Kodunuzu Belgeleme (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- XML [Visual Basic], documenting code
- XML comments, Visual Basic
- Visual Basic code, documenting with XML
ms.assetid: a0d35dc7-c5f9-4d74-92ff-a1c6f28d5235
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 645dd4a8a9d1c78fd54f0f31ad0efd772b671d39
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="documenting-your-code-with-xml-visual-basic"></a><span data-ttu-id="0eaf0-102">XML ile Kodunuzu Belgeleme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0eaf0-102">Documenting Your Code with XML (Visual Basic)</span></span>
<span data-ttu-id="0eaf0-103">Visual Basic'te XML kullanarak kodunuzu belgeleme</span><span class="sxs-lookup"><span data-stu-id="0eaf0-103">In Visual Basic, you can document your code using XML</span></span>  
  
## <a name="xml-documentation-comments"></a><span data-ttu-id="0eaf0-104">XML Belgeleri Yorumları</span><span class="sxs-lookup"><span data-stu-id="0eaf0-104">XML Documentation Comments</span></span>  
 <span data-ttu-id="0eaf0-105">Visual Basic projeleri için XML belgeleri otomatik olarak oluşturmak için kolay bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="0eaf0-105">Visual Basic provides an easy way to automatically create XML documentation for projects.</span></span> <span data-ttu-id="0eaf0-106">Bir XML çatıyı türleri ve üyeleri için otomatik olarak oluşturmak ve ardından her bir parametreyi ve diğer açıklamalar için özetleri, açıklayıcı belgeleri sağlayın.</span><span class="sxs-lookup"><span data-stu-id="0eaf0-106">You can automatically generate an XML skeleton for your types and members, and then provide summaries, descriptive documentation for each parameter, and other remarks.</span></span> <span data-ttu-id="0eaf0-107">Uygun Kurulum'a XML belgeleri otomatik olarak projeniz ve .xml uzantısına aynı ada sahip bir XML dosyasına yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="0eaf0-107">With the appropriate setup, the XML documentation is automatically emitted into an XML file with the same name as your project and the .xml extension.</span></span> <span data-ttu-id="0eaf0-108">Daha fazla bilgi için bkz: [/doc](../../../visual-basic/reference/command-line-compiler/doc.md).</span><span class="sxs-lookup"><span data-stu-id="0eaf0-108">For more information, see [/doc](../../../visual-basic/reference/command-line-compiler/doc.md).</span></span>  
  
 <span data-ttu-id="0eaf0-109">XML dosyasını tüketilen veya aksi halde XML olarak yönetilebilir.</span><span class="sxs-lookup"><span data-stu-id="0eaf0-109">The XML file can be consumed or otherwise manipulated as XML.</span></span> <span data-ttu-id="0eaf0-110">Bu dosya, projenizin çıktı .exe veya .dll dosyası ile aynı dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="0eaf0-110">This file is located in the same directory as the output .exe or .dll file of your project.</span></span>  
  
 <span data-ttu-id="0eaf0-111">XML belgeleri ile başlayan `'''`.</span><span class="sxs-lookup"><span data-stu-id="0eaf0-111">XML documentation starts with `'''`.</span></span> <span data-ttu-id="0eaf0-112">Bu açıklamalar işlenmesini bazı kısıtlamaları vardır:</span><span class="sxs-lookup"><span data-stu-id="0eaf0-112">The processing of these comments has some restrictions:</span></span>  
  
-   <span data-ttu-id="0eaf0-113">Belge doğru biçimlendirilmiş XML.</span><span class="sxs-lookup"><span data-stu-id="0eaf0-113">The documentation must be well-formed XML.</span></span> <span data-ttu-id="0eaf0-114">XML doğru biçimlendirilmemiş, bir uyarı oluşturulur ve bir hatayla karşılaşıldı belirten bir açıklama belge dosyası içerir.</span><span class="sxs-lookup"><span data-stu-id="0eaf0-114">If the XML is not well formed, a warning is generated and the documentation file contains a comment saying that an error was encountered.</span></span>  
  
-   <span data-ttu-id="0eaf0-115">Geliştiriciler kendi etiketleri kümesi oluşturmak boş.</span><span class="sxs-lookup"><span data-stu-id="0eaf0-115">Developers are free to create their own set of tags.</span></span> <span data-ttu-id="0eaf0-116">Önerilen etiketler ("İlgili bölümler" konusuna bakın) birtakım yoktur.</span><span class="sxs-lookup"><span data-stu-id="0eaf0-116">There is a recommended set of tags (see "Related Sections" in this topic).</span></span> <span data-ttu-id="0eaf0-117">Önerilen etiketler bazıları özel anlamlara sahiptir:</span><span class="sxs-lookup"><span data-stu-id="0eaf0-117">Some of the recommended tags have special meanings:</span></span>  
  
    -   <span data-ttu-id="0eaf0-118">\<Param > etiketi parametrelerini tanımlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0eaf0-118">The \<param> tag is used to describe parameters.</span></span> <span data-ttu-id="0eaf0-119">Kullandıysanız, derleyici parametresi var olduğundan ve tüm parametreleri belgelerinde açıklanan doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="0eaf0-119">If used, the compiler will verify that the parameter exists and that all parameters are described in the documentation.</span></span> <span data-ttu-id="0eaf0-120">Doğrulama başarısız olursa, derleyici bir uyarı verir.</span><span class="sxs-lookup"><span data-stu-id="0eaf0-120">If the verification fails, the compiler issues a warning.</span></span>  
  
    -   <span data-ttu-id="0eaf0-121">`cref` Öznitelik, bir başvuru code öğesi sağlamak için herhangi bir etiket için eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="0eaf0-121">The `cref` attribute can be attached to any tag to provide a reference to a code element.</span></span> <span data-ttu-id="0eaf0-122">Derleyici, bu kod öğesi var olduğunu doğrular.</span><span class="sxs-lookup"><span data-stu-id="0eaf0-122">The compiler verifies that this code element exists.</span></span> <span data-ttu-id="0eaf0-123">Doğrulama başarısız olursa, derleyici bir uyarı verir.</span><span class="sxs-lookup"><span data-stu-id="0eaf0-123">If the verification fails, the compiler issues a warning.</span></span> <span data-ttu-id="0eaf0-124">Derleyici de herhangi uyar `Imports` içinde tanımlanan bir tür ararken deyimleri `cref` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="0eaf0-124">The compiler also respects any `Imports` statements when looking for a type described in the `cref` attribute.</span></span>  
  
    -   <span data-ttu-id="0eaf0-125">\<Özet > etiketi IntelliSense içinde tarafından kullanılan [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] bir tür veya üye hakkında ek bilgi görüntülemek için.</span><span class="sxs-lookup"><span data-stu-id="0eaf0-125">The \<summary> tag is used by IntelliSense in [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] to display additional information about a type or member.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="0eaf0-126">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="0eaf0-126">Related Sections</span></span>  
 <span data-ttu-id="0eaf0-127">Belge açıklamaları bir XML dosyası oluşturma hakkında daha fazla bilgi için aşağıdaki konulara bakın:</span><span class="sxs-lookup"><span data-stu-id="0eaf0-127">For details on creating an XML file with documentation comments, see the following topics:</span></span>  
  
-   [<span data-ttu-id="0eaf0-128">/doc</span><span class="sxs-lookup"><span data-stu-id="0eaf0-128">/doc</span></span>](../../../visual-basic/reference/command-line-compiler/doc.md)  
  
-   [<span data-ttu-id="0eaf0-129">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="0eaf0-129">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)  
  
-   [<span data-ttu-id="0eaf0-130">XML Dosyasını İşleme</span><span class="sxs-lookup"><span data-stu-id="0eaf0-130">Processing the XML File</span></span>](../../../visual-basic/programming-guide/program-structure/processing-the-xml-file.md)  
  
-   [<span data-ttu-id="0eaf0-131">Nasıl yapılır: XML Belgesi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="0eaf0-131">How to: Create XML Documentation</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)  
  
-   [<span data-ttu-id="0eaf0-132">Visual Studio'daki XML Araçları</span><span class="sxs-lookup"><span data-stu-id="0eaf0-132">XML Tools in Visual Studio</span></span>](/visualstudio/xml-tools/xml-tools-in-visual-studio)  
  
## <a name="see-also"></a><span data-ttu-id="0eaf0-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0eaf0-133">See Also</span></span>  
 [<span data-ttu-id="0eaf0-134">Visual Basic ile uygulamaları geliştirme</span><span class="sxs-lookup"><span data-stu-id="0eaf0-134">Developing Applications with Visual Basic</span></span>](../../../visual-basic/developing-apps/index.md)  
 [<span data-ttu-id="0eaf0-135">Visual Basic programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="0eaf0-135">Visual Basic Programming Guide</span></span>](../../../visual-basic/programming-guide/index.md)
