---
title: XML ile Kodunuzu Belgeleme
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], documenting code
- XML comments, Visual Basic
- Visual Basic code, documenting with XML
ms.assetid: a0d35dc7-c5f9-4d74-92ff-a1c6f28d5235
ms.openlocfilehash: f391fb909cfe4de8f27afb24d6db389e2c8cdfae
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84590935"
---
# <a name="document-your-code-with-xml-visual-basic"></a><span data-ttu-id="da9f9-102">Kodunuzu XML ile belgeleyin (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="da9f9-102">Document your code with XML (Visual Basic)</span></span>

<span data-ttu-id="da9f9-103">Visual Basic, kodunuzu XML kullanarak belgeedebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="da9f9-103">In Visual Basic, you can document your code using XML.</span></span>

## <a name="xml-documentation-comments"></a><span data-ttu-id="da9f9-104">XML belgeleri yorumları</span><span class="sxs-lookup"><span data-stu-id="da9f9-104">XML documentation comments</span></span>

<span data-ttu-id="da9f9-105">Visual Basic, projeler için otomatik olarak XML belgelerinin oluşturulması için kolay bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="da9f9-105">Visual Basic provides an easy way to automatically create XML documentation for projects.</span></span> <span data-ttu-id="da9f9-106">Türleriniz ve üyelerinize yönelik otomatik olarak bir XML iskelet oluşturabilir, ardından her bir parametre için özetler, açıklayıcı belgeler ve diğer açıklamalar sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="da9f9-106">You can automatically generate an XML skeleton for your types and members, and then provide summaries, descriptive documentation for each parameter, and other remarks.</span></span> <span data-ttu-id="da9f9-107">Uygun kurulumla, XML belgeleri projenizle aynı kök dosya adına sahip bir XML dosyasına otomatik olarak yayılır.</span><span class="sxs-lookup"><span data-stu-id="da9f9-107">With the appropriate setup, the XML documentation is automatically emitted into an XML file with the same root file name as your project.</span></span> <span data-ttu-id="da9f9-108">Daha fazla bilgi için bkz. [-doc](../../reference/command-line-compiler/doc.md).</span><span class="sxs-lookup"><span data-stu-id="da9f9-108">For more information, see [-doc](../../reference/command-line-compiler/doc.md).</span></span>

<span data-ttu-id="da9f9-109">XML dosyası, XML olarak tüketilebilir veya başka bir şekilde yönetilebilir.</span><span class="sxs-lookup"><span data-stu-id="da9f9-109">The XML file can be consumed or otherwise manipulated as XML.</span></span> <span data-ttu-id="da9f9-110">Bu dosya, projenizin output. exe veya. dll dosyası ile aynı dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="da9f9-110">This file is located in the same directory as the output .exe or .dll file of your project.</span></span>

<span data-ttu-id="da9f9-111">XML belgeleri ile başlar `'''` .</span><span class="sxs-lookup"><span data-stu-id="da9f9-111">XML documentation starts with `'''`.</span></span> <span data-ttu-id="da9f9-112">Bu yorumların işlenmesinde bazı kısıtlamalar vardır:</span><span class="sxs-lookup"><span data-stu-id="da9f9-112">The processing of these comments has some restrictions:</span></span>

- <span data-ttu-id="da9f9-113">Belgeler düzgün biçimlendirilmiş XML olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="da9f9-113">The documentation must be well-formed XML.</span></span> <span data-ttu-id="da9f9-114">XML düzgün biçimlendirilmediyse bir uyarı oluşturulur ve belge dosyası bir hata ile karşılaşıldığını söyleyen bir açıklama içerir.</span><span class="sxs-lookup"><span data-stu-id="da9f9-114">If the XML is not well formed, a warning is generated and the documentation file contains a comment saying that an error was encountered.</span></span>

- <span data-ttu-id="da9f9-115">Geliştiriciler kendi etiket kümesini oluşturmak ücretsizdir.</span><span class="sxs-lookup"><span data-stu-id="da9f9-115">Developers are free to create their own set of tags.</span></span> <span data-ttu-id="da9f9-116">Önerilen bir etiket kümesi vardır (bkz. [XML açıklama etiketleri](../../language-reference/xmldoc/index.md)).</span><span class="sxs-lookup"><span data-stu-id="da9f9-116">There is a recommended set of tags (see [XML Comment Tags](../../language-reference/xmldoc/index.md)).</span></span> <span data-ttu-id="da9f9-117">Önerilen etiketlerden bazılarının özel anlamları vardır:</span><span class="sxs-lookup"><span data-stu-id="da9f9-117">Some of the recommended tags have special meanings:</span></span>

  - <span data-ttu-id="da9f9-118">\<param>Etiketi, parametreleri tanımlamakta kullanılır.</span><span class="sxs-lookup"><span data-stu-id="da9f9-118">The \<param> tag is used to describe parameters.</span></span> <span data-ttu-id="da9f9-119">Kullanıldıysa, derleyici parametrenin var olduğunu ve tüm parametrelerin belgelerde açıklananlandığından emin olur.</span><span class="sxs-lookup"><span data-stu-id="da9f9-119">If used, the compiler will verify that the parameter exists and that all parameters are described in the documentation.</span></span> <span data-ttu-id="da9f9-120">Doğrulama başarısız olursa, derleyici bir uyarı verir.</span><span class="sxs-lookup"><span data-stu-id="da9f9-120">If the verification fails, the compiler issues a warning.</span></span>

  - <span data-ttu-id="da9f9-121">`cref`Özniteliği bir kod öğesine başvuru sağlamak için herhangi bir etikete iliştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="da9f9-121">The `cref` attribute can be attached to any tag to provide a reference to a code element.</span></span> <span data-ttu-id="da9f9-122">Derleyici bu kod öğesinin varolduğunu doğrular.</span><span class="sxs-lookup"><span data-stu-id="da9f9-122">The compiler verifies that this code element exists.</span></span> <span data-ttu-id="da9f9-123">Doğrulama başarısız olursa, derleyici bir uyarı verir.</span><span class="sxs-lookup"><span data-stu-id="da9f9-123">If the verification fails, the compiler issues a warning.</span></span> <span data-ttu-id="da9f9-124">Derleyici, `Imports` özniteliğinde açıklanan bir tür ararken de herhangi bir deyime uyar `cref` .</span><span class="sxs-lookup"><span data-stu-id="da9f9-124">The compiler also respects any `Imports` statements when looking for a type described in the `cref` attribute.</span></span>

  - <span data-ttu-id="da9f9-125">\<summary>Etiketi, Visual Studio 'Da IntelliSense tarafından bir tür veya üyeyle ilgili ek bilgileri göstermek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="da9f9-125">The \<summary> tag is used by IntelliSense in Visual Studio to display additional information about a type or member.</span></span>

## <a name="related-sections"></a><span data-ttu-id="da9f9-126">İlgili bölümler</span><span class="sxs-lookup"><span data-stu-id="da9f9-126">Related sections</span></span>

<span data-ttu-id="da9f9-127">Belge açıklamalarıyla bir XML dosyası oluşturma hakkında daha fazla bilgi için aşağıdaki konulara bakın:</span><span class="sxs-lookup"><span data-stu-id="da9f9-127">For details on creating an XML file with documentation comments, see the following topics:</span></span>

- [<span data-ttu-id="da9f9-128">-doc</span><span class="sxs-lookup"><span data-stu-id="da9f9-128">-doc</span></span>](../../reference/command-line-compiler/doc.md)

- [<span data-ttu-id="da9f9-129">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="da9f9-129">XML Comment Tags</span></span>](../../language-reference/xmldoc/index.md)

- [<span data-ttu-id="da9f9-130">XML dosyası işleniyor</span><span class="sxs-lookup"><span data-stu-id="da9f9-130">Processing the XML File</span></span>](processing-the-xml-file.md)

- [<span data-ttu-id="da9f9-131">Nasıl yapılır: XML Belgesi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="da9f9-131">How to: Create XML Documentation</span></span>](how-to-create-xml-documentation.md)

- [<span data-ttu-id="da9f9-132">Visual Studio'daki XML Araçları</span><span class="sxs-lookup"><span data-stu-id="da9f9-132">XML Tools in Visual Studio</span></span>](/visualstudio/xml-tools/xml-tools-in-visual-studio)

## <a name="see-also"></a><span data-ttu-id="da9f9-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="da9f9-133">See also</span></span>

- [<span data-ttu-id="da9f9-134">Visual Basic ile Uygulama Geliştirme</span><span class="sxs-lookup"><span data-stu-id="da9f9-134">Developing Applications with Visual Basic</span></span>](../../developing-apps/index.md)
- [<span data-ttu-id="da9f9-135">Visual Basic Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="da9f9-135">Visual Basic Programming Guide</span></span>](../index.md)
