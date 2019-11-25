---
title: XML ile Kodunuzu Belgeleme
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], documenting code
- XML comments, Visual Basic
- Visual Basic code, documenting with XML
ms.assetid: a0d35dc7-c5f9-4d74-92ff-a1c6f28d5235
ms.openlocfilehash: bdf0da7a8acc919e4a1d66b81e30c9ed912dd321
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347448"
---
# <a name="documenting-your-code-with-xml-visual-basic"></a><span data-ttu-id="5a980-102">XML ile Kodunuzu Belgeleme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5a980-102">Documenting Your Code with XML (Visual Basic)</span></span>

<span data-ttu-id="5a980-103">In Visual Basic, you can document your code using XML</span><span class="sxs-lookup"><span data-stu-id="5a980-103">In Visual Basic, you can document your code using XML</span></span>

## <a name="xml-documentation-comments"></a><span data-ttu-id="5a980-104">XML Belgeleri Yorumları</span><span class="sxs-lookup"><span data-stu-id="5a980-104">XML Documentation Comments</span></span>

<span data-ttu-id="5a980-105">Visual Basic provides an easy way to automatically create XML documentation for projects.</span><span class="sxs-lookup"><span data-stu-id="5a980-105">Visual Basic provides an easy way to automatically create XML documentation for projects.</span></span> <span data-ttu-id="5a980-106">You can automatically generate an XML skeleton for your types and members, and then provide summaries, descriptive documentation for each parameter, and other remarks.</span><span class="sxs-lookup"><span data-stu-id="5a980-106">You can automatically generate an XML skeleton for your types and members, and then provide summaries, descriptive documentation for each parameter, and other remarks.</span></span> <span data-ttu-id="5a980-107">With the appropriate setup, the XML documentation is automatically emitted into an XML file with the same name as your project and the .xml extension.</span><span class="sxs-lookup"><span data-stu-id="5a980-107">With the appropriate setup, the XML documentation is automatically emitted into an XML file with the same name as your project and the .xml extension.</span></span> <span data-ttu-id="5a980-108">For more information, see [-doc](../../../visual-basic/reference/command-line-compiler/doc.md).</span><span class="sxs-lookup"><span data-stu-id="5a980-108">For more information, see [-doc](../../../visual-basic/reference/command-line-compiler/doc.md).</span></span>

<span data-ttu-id="5a980-109">The XML file can be consumed or otherwise manipulated as XML.</span><span class="sxs-lookup"><span data-stu-id="5a980-109">The XML file can be consumed or otherwise manipulated as XML.</span></span> <span data-ttu-id="5a980-110">This file is located in the same directory as the output .exe or .dll file of your project.</span><span class="sxs-lookup"><span data-stu-id="5a980-110">This file is located in the same directory as the output .exe or .dll file of your project.</span></span>

<span data-ttu-id="5a980-111">XML documentation starts with `'''`.</span><span class="sxs-lookup"><span data-stu-id="5a980-111">XML documentation starts with `'''`.</span></span> <span data-ttu-id="5a980-112">The processing of these comments has some restrictions:</span><span class="sxs-lookup"><span data-stu-id="5a980-112">The processing of these comments has some restrictions:</span></span>

- <span data-ttu-id="5a980-113">The documentation must be well-formed XML.</span><span class="sxs-lookup"><span data-stu-id="5a980-113">The documentation must be well-formed XML.</span></span> <span data-ttu-id="5a980-114">If the XML is not well formed, a warning is generated and the documentation file contains a comment saying that an error was encountered.</span><span class="sxs-lookup"><span data-stu-id="5a980-114">If the XML is not well formed, a warning is generated and the documentation file contains a comment saying that an error was encountered.</span></span>

- <span data-ttu-id="5a980-115">Developers are free to create their own set of tags.</span><span class="sxs-lookup"><span data-stu-id="5a980-115">Developers are free to create their own set of tags.</span></span> <span data-ttu-id="5a980-116">There is a recommended set of tags (see "Related Sections" in this topic).</span><span class="sxs-lookup"><span data-stu-id="5a980-116">There is a recommended set of tags (see "Related Sections" in this topic).</span></span> <span data-ttu-id="5a980-117">Some of the recommended tags have special meanings:</span><span class="sxs-lookup"><span data-stu-id="5a980-117">Some of the recommended tags have special meanings:</span></span>

  - <span data-ttu-id="5a980-118">The \<param> tag is used to describe parameters.</span><span class="sxs-lookup"><span data-stu-id="5a980-118">The \<param> tag is used to describe parameters.</span></span> <span data-ttu-id="5a980-119">If used, the compiler will verify that the parameter exists and that all parameters are described in the documentation.</span><span class="sxs-lookup"><span data-stu-id="5a980-119">If used, the compiler will verify that the parameter exists and that all parameters are described in the documentation.</span></span> <span data-ttu-id="5a980-120">If the verification fails, the compiler issues a warning.</span><span class="sxs-lookup"><span data-stu-id="5a980-120">If the verification fails, the compiler issues a warning.</span></span>

  - <span data-ttu-id="5a980-121">The `cref` attribute can be attached to any tag to provide a reference to a code element.</span><span class="sxs-lookup"><span data-stu-id="5a980-121">The `cref` attribute can be attached to any tag to provide a reference to a code element.</span></span> <span data-ttu-id="5a980-122">The compiler verifies that this code element exists.</span><span class="sxs-lookup"><span data-stu-id="5a980-122">The compiler verifies that this code element exists.</span></span> <span data-ttu-id="5a980-123">If the verification fails, the compiler issues a warning.</span><span class="sxs-lookup"><span data-stu-id="5a980-123">If the verification fails, the compiler issues a warning.</span></span> <span data-ttu-id="5a980-124">The compiler also respects any `Imports` statements when looking for a type described in the `cref` attribute.</span><span class="sxs-lookup"><span data-stu-id="5a980-124">The compiler also respects any `Imports` statements when looking for a type described in the `cref` attribute.</span></span>

  - <span data-ttu-id="5a980-125">The \<summary> tag is used by IntelliSense in Visual Studio to display additional information about a type or member.</span><span class="sxs-lookup"><span data-stu-id="5a980-125">The \<summary> tag is used by IntelliSense in Visual Studio to display additional information about a type or member.</span></span>

## <a name="related-sections"></a><span data-ttu-id="5a980-126">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="5a980-126">Related Sections</span></span>

<span data-ttu-id="5a980-127">For details on creating an XML file with documentation comments, see the following topics:</span><span class="sxs-lookup"><span data-stu-id="5a980-127">For details on creating an XML file with documentation comments, see the following topics:</span></span>

- [<span data-ttu-id="5a980-128">-doc</span><span class="sxs-lookup"><span data-stu-id="5a980-128">-doc</span></span>](../../../visual-basic/reference/command-line-compiler/doc.md)

- [<span data-ttu-id="5a980-129">XML Açıklama Etiketleri</span><span class="sxs-lookup"><span data-stu-id="5a980-129">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)

- [<span data-ttu-id="5a980-130">XML Dosyasını İşleme</span><span class="sxs-lookup"><span data-stu-id="5a980-130">Processing the XML File</span></span>](../../../visual-basic/programming-guide/program-structure/processing-the-xml-file.md)

- [<span data-ttu-id="5a980-131">Nasıl yapılır: XML Belgesi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="5a980-131">How to: Create XML Documentation</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)

- [<span data-ttu-id="5a980-132">Visual Studio'daki XML Araçları</span><span class="sxs-lookup"><span data-stu-id="5a980-132">XML Tools in Visual Studio</span></span>](/visualstudio/xml-tools/xml-tools-in-visual-studio)

## <a name="see-also"></a><span data-ttu-id="5a980-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5a980-133">See also</span></span>

- [<span data-ttu-id="5a980-134">Developing Applications with Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5a980-134">Developing Applications with Visual Basic</span></span>](../../../visual-basic/developing-apps/index.md)
- [<span data-ttu-id="5a980-135">Visual Basic Programming Guide</span><span class="sxs-lookup"><span data-stu-id="5a980-135">Visual Basic Programming Guide</span></span>](../../../visual-basic/programming-guide/index.md)
