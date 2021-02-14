---
description: 'Hakkında daha fazla bilgi edinin: kodunuzu XML ile belgeleme (Visual Basic)'
title: XML ile Kodunuzu Belgeleme
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], documenting code
- XML comments, Visual Basic
- Visual Basic code, documenting with XML
ms.assetid: a0d35dc7-c5f9-4d74-92ff-a1c6f28d5235
ms.openlocfilehash: b554007bdd5183d0d92dc7ff62d08885f4b7f486
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100476013"
---
# <a name="document-your-code-with-xml-visual-basic"></a><span data-ttu-id="5ef3a-103">Kodunuzu XML ile belgeleyin (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5ef3a-103">Document your code with XML (Visual Basic)</span></span>

<span data-ttu-id="5ef3a-104">Visual Basic, kodunuzu XML kullanarak belgeedebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5ef3a-104">In Visual Basic, you can document your code using XML.</span></span>

## <a name="xml-documentation-comments"></a><span data-ttu-id="5ef3a-105">XML belgeleri yorumları</span><span class="sxs-lookup"><span data-stu-id="5ef3a-105">XML documentation comments</span></span>

<span data-ttu-id="5ef3a-106">Visual Basic, projeler için otomatik olarak XML belgelerinin oluşturulması için kolay bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="5ef3a-106">Visual Basic provides an easy way to automatically create XML documentation for projects.</span></span> <span data-ttu-id="5ef3a-107">Türleriniz ve üyelerinize yönelik otomatik olarak bir XML iskelet oluşturabilir, ardından her bir parametre için özetler, açıklayıcı belgeler ve diğer açıklamalar sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5ef3a-107">You can automatically generate an XML skeleton for your types and members, and then provide summaries, descriptive documentation for each parameter, and other remarks.</span></span> <span data-ttu-id="5ef3a-108">Uygun kurulumla, XML belgeleri projenizle aynı kök dosya adına sahip bir XML dosyasına otomatik olarak yayılır.</span><span class="sxs-lookup"><span data-stu-id="5ef3a-108">With the appropriate setup, the XML documentation is automatically emitted into an XML file with the same root file name as your project.</span></span> <span data-ttu-id="5ef3a-109">Daha fazla bilgi için bkz. [-doc](../../reference/command-line-compiler/doc.md).</span><span class="sxs-lookup"><span data-stu-id="5ef3a-109">For more information, see [-doc](../../reference/command-line-compiler/doc.md).</span></span>

<span data-ttu-id="5ef3a-110">XML dosyası, XML olarak tüketilebilir veya başka bir şekilde yönetilebilir.</span><span class="sxs-lookup"><span data-stu-id="5ef3a-110">The XML file can be consumed or otherwise manipulated as XML.</span></span> <span data-ttu-id="5ef3a-111">Bu dosya, projenizin output. exe veya. dll dosyası ile aynı dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="5ef3a-111">This file is located in the same directory as the output .exe or .dll file of your project.</span></span>

<span data-ttu-id="5ef3a-112">XML belgeleri ile başlar `'''` .</span><span class="sxs-lookup"><span data-stu-id="5ef3a-112">XML documentation starts with `'''`.</span></span> <span data-ttu-id="5ef3a-113">Bu yorumların işlenmesinde bazı kısıtlamalar vardır:</span><span class="sxs-lookup"><span data-stu-id="5ef3a-113">The processing of these comments has some restrictions:</span></span>

- <span data-ttu-id="5ef3a-114">Belgeler düzgün biçimlendirilmiş XML olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5ef3a-114">The documentation must be well-formed XML.</span></span> <span data-ttu-id="5ef3a-115">XML düzgün biçimlendirilmediyse bir uyarı oluşturulur ve belge dosyası bir hata ile karşılaşıldığını söyleyen bir açıklama içerir.</span><span class="sxs-lookup"><span data-stu-id="5ef3a-115">If the XML is not well formed, a warning is generated and the documentation file contains a comment saying that an error was encountered.</span></span>

- <span data-ttu-id="5ef3a-116">Geliştiriciler kendi etiket kümesini oluşturmak ücretsizdir.</span><span class="sxs-lookup"><span data-stu-id="5ef3a-116">Developers are free to create their own set of tags.</span></span> <span data-ttu-id="5ef3a-117">Önerilen bir etiket kümesi vardır (bkz. [XML açıklama etiketleri](../../language-reference/xmldoc/index.md)).</span><span class="sxs-lookup"><span data-stu-id="5ef3a-117">There is a recommended set of tags (see [XML Comment Tags](../../language-reference/xmldoc/index.md)).</span></span> <span data-ttu-id="5ef3a-118">Önerilen etiketlerden bazılarının özel anlamları vardır:</span><span class="sxs-lookup"><span data-stu-id="5ef3a-118">Some of the recommended tags have special meanings:</span></span>

  - <span data-ttu-id="5ef3a-119">\<param>Etiketi, parametreleri tanımlamakta kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5ef3a-119">The \<param> tag is used to describe parameters.</span></span> <span data-ttu-id="5ef3a-120">Kullanıldıysa, derleyici parametrenin var olduğunu ve tüm parametrelerin belgelerde açıklananlandığından emin olur.</span><span class="sxs-lookup"><span data-stu-id="5ef3a-120">If used, the compiler will verify that the parameter exists and that all parameters are described in the documentation.</span></span> <span data-ttu-id="5ef3a-121">Doğrulama başarısız olursa, derleyici bir uyarı verir.</span><span class="sxs-lookup"><span data-stu-id="5ef3a-121">If the verification fails, the compiler issues a warning.</span></span>

  - <span data-ttu-id="5ef3a-122">`cref`Özniteliği bir kod öğesine başvuru sağlamak için herhangi bir etikete iliştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="5ef3a-122">The `cref` attribute can be attached to any tag to provide a reference to a code element.</span></span> <span data-ttu-id="5ef3a-123">Derleyici bu kod öğesinin varolduğunu doğrular.</span><span class="sxs-lookup"><span data-stu-id="5ef3a-123">The compiler verifies that this code element exists.</span></span> <span data-ttu-id="5ef3a-124">Doğrulama başarısız olursa, derleyici bir uyarı verir.</span><span class="sxs-lookup"><span data-stu-id="5ef3a-124">If the verification fails, the compiler issues a warning.</span></span> <span data-ttu-id="5ef3a-125">Derleyici, `Imports` özniteliğinde açıklanan bir tür ararken de herhangi bir deyime uyar `cref` .</span><span class="sxs-lookup"><span data-stu-id="5ef3a-125">The compiler also respects any `Imports` statements when looking for a type described in the `cref` attribute.</span></span>

  - <span data-ttu-id="5ef3a-126">\<summary>Etiketi, Visual Studio 'Da IntelliSense tarafından bir tür veya üyeyle ilgili ek bilgileri göstermek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5ef3a-126">The \<summary> tag is used by IntelliSense in Visual Studio to display additional information about a type or member.</span></span>

## <a name="related-sections"></a><span data-ttu-id="5ef3a-127">İlgili bölümler</span><span class="sxs-lookup"><span data-stu-id="5ef3a-127">Related sections</span></span>

<span data-ttu-id="5ef3a-128">Belge açıklamalarıyla bir XML dosyası oluşturma hakkında daha fazla bilgi için aşağıdaki konulara bakın:</span><span class="sxs-lookup"><span data-stu-id="5ef3a-128">For details on creating an XML file with documentation comments, see the following topics:</span></span>

- [<span data-ttu-id="5ef3a-129">-doc</span><span class="sxs-lookup"><span data-stu-id="5ef3a-129">-doc</span></span>](../../reference/command-line-compiler/doc.md)

- [<span data-ttu-id="5ef3a-130">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="5ef3a-130">XML Comment Tags</span></span>](../../language-reference/xmldoc/index.md)

- [<span data-ttu-id="5ef3a-131">XML dosyası işleniyor</span><span class="sxs-lookup"><span data-stu-id="5ef3a-131">Processing the XML File</span></span>](processing-the-xml-file.md)

- [<span data-ttu-id="5ef3a-132">Nasıl yapılır: XML Belgesi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="5ef3a-132">How to: Create XML Documentation</span></span>](how-to-create-xml-documentation.md)

- [<span data-ttu-id="5ef3a-133">Visual Studio 'da XML araçları</span><span class="sxs-lookup"><span data-stu-id="5ef3a-133">XML Tools in Visual Studio</span></span>](/visualstudio/xml-tools/xml-tools-in-visual-studio)

## <a name="see-also"></a><span data-ttu-id="5ef3a-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5ef3a-134">See also</span></span>

- [<span data-ttu-id="5ef3a-135">Visual Basic ile Uygulama Geliştirme</span><span class="sxs-lookup"><span data-stu-id="5ef3a-135">Developing Applications with Visual Basic</span></span>](../../developing-apps/index.md)
- [<span data-ttu-id="5ef3a-136">Visual Basic Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="5ef3a-136">Visual Basic Programming Guide</span></span>](../index.md)
