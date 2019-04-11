---
title: XML ile Kodunuzu Belgeleme (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], documenting code
- XML comments, Visual Basic
- Visual Basic code, documenting with XML
ms.assetid: a0d35dc7-c5f9-4d74-92ff-a1c6f28d5235
ms.openlocfilehash: 6b9fe9994b7bdf2259dcdb1ecef906e0f9955c8f
ms.sourcegitcommit: 859b2ba0c74a1a5a4ad0d59a3c3af23450995981
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59480631"
---
# <a name="documenting-your-code-with-xml-visual-basic"></a><span data-ttu-id="59128-102">XML ile Kodunuzu Belgeleme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="59128-102">Documenting Your Code with XML (Visual Basic)</span></span>

<span data-ttu-id="59128-103">Visual Basic'te XML kullanarak kodunuzu belgeleme</span><span class="sxs-lookup"><span data-stu-id="59128-103">In Visual Basic, you can document your code using XML</span></span>

## <a name="xml-documentation-comments"></a><span data-ttu-id="59128-104">XML Belgeleri Yorumları</span><span class="sxs-lookup"><span data-stu-id="59128-104">XML Documentation Comments</span></span>

<span data-ttu-id="59128-105">Visual Basic projeleri için XML belgeleri otomatik olarak oluşturmak için kolay bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="59128-105">Visual Basic provides an easy way to automatically create XML documentation for projects.</span></span> <span data-ttu-id="59128-106">Bir XML skeleton türler ve üyeler için otomatik olarak oluşturmak ve özetleri, açıklayıcı belgeleri her parametre ve diğer açıklamalar sağlar.</span><span class="sxs-lookup"><span data-stu-id="59128-106">You can automatically generate an XML skeleton for your types and members, and then provide summaries, descriptive documentation for each parameter, and other remarks.</span></span> <span data-ttu-id="59128-107">Uygun Kurulum, XML belgeleri projenizi ve .xml uzantısı olarak aynı ada sahip bir XML dosyasına otomatik olarak yayılır.</span><span class="sxs-lookup"><span data-stu-id="59128-107">With the appropriate setup, the XML documentation is automatically emitted into an XML file with the same name as your project and the .xml extension.</span></span> <span data-ttu-id="59128-108">Daha fazla bilgi için [/doc](../../../visual-basic/reference/command-line-compiler/doc.md).</span><span class="sxs-lookup"><span data-stu-id="59128-108">For more information, see [/doc](../../../visual-basic/reference/command-line-compiler/doc.md).</span></span>

<span data-ttu-id="59128-109">XML dosyası kullanılan veya aksi halde XML olarak yönetilebilir.</span><span class="sxs-lookup"><span data-stu-id="59128-109">The XML file can be consumed or otherwise manipulated as XML.</span></span> <span data-ttu-id="59128-110">Bu dosya, projenizin çıkış .exe veya .dll dosyası ile aynı dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="59128-110">This file is located in the same directory as the output .exe or .dll file of your project.</span></span>

<span data-ttu-id="59128-111">XML belgeleri ile başlayan `'''`.</span><span class="sxs-lookup"><span data-stu-id="59128-111">XML documentation starts with `'''`.</span></span> <span data-ttu-id="59128-112">Bu açıklamalar işlenmesini bazı kısıtlamalar mevcuttur:</span><span class="sxs-lookup"><span data-stu-id="59128-112">The processing of these comments has some restrictions:</span></span>

- <span data-ttu-id="59128-113">Belgeler doğru biçimlendirilmiş XML.</span><span class="sxs-lookup"><span data-stu-id="59128-113">The documentation must be well-formed XML.</span></span> <span data-ttu-id="59128-114">XML düzgün biçimlendirilmemiş ise bir uyarı oluşturulur ve belge dosyası bir hatayla karşılaşıldı belirten bir açıklama içerir.</span><span class="sxs-lookup"><span data-stu-id="59128-114">If the XML is not well formed, a warning is generated and the documentation file contains a comment saying that an error was encountered.</span></span>

- <span data-ttu-id="59128-115">Geliştiriciler kendi kümesi etiketleri oluşturmak ücretsizdir.</span><span class="sxs-lookup"><span data-stu-id="59128-115">Developers are free to create their own set of tags.</span></span> <span data-ttu-id="59128-116">Önerilen etiketler ("İlgili bölümler" bölümüne bakın) kümesi yok.</span><span class="sxs-lookup"><span data-stu-id="59128-116">There is a recommended set of tags (see "Related Sections" in this topic).</span></span> <span data-ttu-id="59128-117">Önerilen etiketler bazıları, özel anlamları vardır:</span><span class="sxs-lookup"><span data-stu-id="59128-117">Some of the recommended tags have special meanings:</span></span>

  - <span data-ttu-id="59128-118">\<Param > etiketi, parametreler tanımlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="59128-118">The \<param> tag is used to describe parameters.</span></span> <span data-ttu-id="59128-119">Kullandıysanız, derleyici parametresi var olduğundan ve tüm parametreleri belgelerinde açıklanan doğrulayın.</span><span class="sxs-lookup"><span data-stu-id="59128-119">If used, the compiler will verify that the parameter exists and that all parameters are described in the documentation.</span></span> <span data-ttu-id="59128-120">Doğrulama başarısız olursa, derleyici bir uyarı verir.</span><span class="sxs-lookup"><span data-stu-id="59128-120">If the verification fails, the compiler issues a warning.</span></span>

  - <span data-ttu-id="59128-121">`cref` Öznitelik, bir kod öğesi başvuru sağlamak için herhangi bir etiket eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="59128-121">The `cref` attribute can be attached to any tag to provide a reference to a code element.</span></span> <span data-ttu-id="59128-122">Derleyici, bu kod öğesi var olduğunu doğrular.</span><span class="sxs-lookup"><span data-stu-id="59128-122">The compiler verifies that this code element exists.</span></span> <span data-ttu-id="59128-123">Doğrulama başarısız olursa, derleyici bir uyarı verir.</span><span class="sxs-lookup"><span data-stu-id="59128-123">If the verification fails, the compiler issues a warning.</span></span> <span data-ttu-id="59128-124">Derleyici ayrıca tüm uyar `Imports` içinde tanımlanan bir tür ararken deyimleri `cref` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="59128-124">The compiler also respects any `Imports` statements when looking for a type described in the `cref` attribute.</span></span>

  - <span data-ttu-id="59128-125">\<Özet > etiketi Visual Studio IntelliSense tarafından bir tür veya üyeyle ilgili ek bilgileri görüntülemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="59128-125">The \<summary> tag is used by IntelliSense in Visual Studio to display additional information about a type or member.</span></span>

## <a name="related-sections"></a><span data-ttu-id="59128-126">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="59128-126">Related Sections</span></span>

<span data-ttu-id="59128-127">Belge açıklamaları bir XML dosyası oluşturma hakkında daha fazla bilgi edinmek için aşağıdaki konulara bakın:</span><span class="sxs-lookup"><span data-stu-id="59128-127">For details on creating an XML file with documentation comments, see the following topics:</span></span>

- [<span data-ttu-id="59128-128">/doc</span><span class="sxs-lookup"><span data-stu-id="59128-128">/doc</span></span>](../../../visual-basic/reference/command-line-compiler/doc.md)

- [<span data-ttu-id="59128-129">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="59128-129">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)

- [<span data-ttu-id="59128-130">XML Dosyasını İşleme</span><span class="sxs-lookup"><span data-stu-id="59128-130">Processing the XML File</span></span>](../../../visual-basic/programming-guide/program-structure/processing-the-xml-file.md)

- [<span data-ttu-id="59128-131">Nasıl yapılır: XML Belgesi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="59128-131">How to: Create XML Documentation</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)

- [<span data-ttu-id="59128-132">Visual Studio'daki XML Araçları</span><span class="sxs-lookup"><span data-stu-id="59128-132">XML Tools in Visual Studio</span></span>](/visualstudio/xml-tools/xml-tools-in-visual-studio)

## <a name="see-also"></a><span data-ttu-id="59128-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="59128-133">See also</span></span>

- [<span data-ttu-id="59128-134">Visual Basic ile Uygulama Geliştirme</span><span class="sxs-lookup"><span data-stu-id="59128-134">Developing Applications with Visual Basic</span></span>](../../../visual-basic/developing-apps/index.md)
- [<span data-ttu-id="59128-135">Visual Basic Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="59128-135">Visual Basic Programming Guide</span></span>](../../../visual-basic/programming-guide/index.md)
