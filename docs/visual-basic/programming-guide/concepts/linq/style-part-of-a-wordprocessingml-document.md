---
title: WordprocessingML Document2 stil kısmı
ms.date: 07/20/2015
ms.assetid: 292cc094-9483-4192-ac3b-a5dc51fbac12
ms.openlocfilehash: 2e5e0e570fa842fb8a4df59d4b1c02e1169c6878
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58838072"
---
# <a name="style-part-of-a-wordprocessingml-document"></a><span data-ttu-id="e99c1-102">WordprocessingML Belgesinin Stil Kısmı</span><span class="sxs-lookup"><span data-stu-id="e99c1-102">Style Part of a WordprocessingML Document</span></span>
<span data-ttu-id="e99c1-103">Bu konuda, Office Open XML WordprocessingML belgesinin stil kısmı örneği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="e99c1-103">This topic shows an example of the style part of the Office Open XML WordprocessingML document.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e99c1-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="e99c1-104">Example</span></span>  
 <span data-ttu-id="e99c1-105">Aşağıdaki örnek bir Office Open XML WordprocessingML belgesinin stil kısmı yapan XML'dir.</span><span class="sxs-lookup"><span data-stu-id="e99c1-105">The following example is the XML that makes up the style part of an Office Open XML WordprocessingML document.</span></span>  
  
 <span data-ttu-id="e99c1-106">Varsayılan paragraf stilini aşağıdaki açılış etiketinde sahip bir öğe vardır:</span><span class="sxs-lookup"><span data-stu-id="e99c1-106">The default paragraph style has an element with the following opening tag:</span></span>  
  
```  
<w:style w:type="paragraph" w:default="1" w:styleId="Normal">  
```  
  
 <span data-ttu-id="e99c1-107">Böylece sorgu varsayılan stil paragraf stilini varsayılan stili tanımlayıcısını bulmak için bir sorgu yazdığınızda bu bilgiye gerekir.</span><span class="sxs-lookup"><span data-stu-id="e99c1-107">You need to know this information when you write the query to find the default style identifier, so that the query can identify the style of paragraphs that have the default style.</span></span>  
  
 <span data-ttu-id="e99c1-108">Bu belgeleri için Microsoft Word oluşturur. tipik belgelerde karşılaştırıldığında çok basit olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="e99c1-108">Note that these documents are very simple when compared to typical documents that Microsoft Word generates.</span></span> <span data-ttu-id="e99c1-109">Çoğu durumda, Word, önemli miktarda ek bilgiler, ek biçimlendirme ve meta verileri kaydeder.</span><span class="sxs-lookup"><span data-stu-id="e99c1-109">In many cases, Word saves a great deal of additional information, additional formatting and metadata.</span></span> <span data-ttu-id="e99c1-110">Ayrıca, bu örnekte olduğu gibi kolay okunabilir olmasını satırları sözcük biçimlendirmez; Bunun yerine, XML, girinti kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="e99c1-110">Furthermore, Word does not format the lines to be easily readable as in this example; instead, the XML is saved without indentation.</span></span> <span data-ttu-id="e99c1-111">Ancak, aynı temel XML şeklin tüm WordprocessingML belgelerinin paylaşır.</span><span class="sxs-lookup"><span data-stu-id="e99c1-111">However, all WordprocessingML documents share the same basic XML shape.</span></span> <span data-ttu-id="e99c1-112">Bu nedenle, bu öğreticide gösterilen sorguları daha karmaşık belgeleri ile çalışır.</span><span class="sxs-lookup"><span data-stu-id="e99c1-112">Because of this, the queries presented in this tutorial will work with more complicated documents.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<w:styles  
    xmlns:r="http://schemas.openxmlformats.org/officeDocument/2006/relationships"  
    xmlns:w="http://schemas.openxmlformats.org/wordprocessingml/2006/main">  
  <w:docDefaults>  
    <w:rPrDefault>  
      <w:rPr>  
        <w:rFonts  
            w:ascii="Times New Roman"  
            w:eastAsia="Times New Roman"  
            w:hAnsi="Times New Roman"  
            w:cs="Times New Roman" />  
        <w:sz w:val="22" />  
        <w:szCs w:val="22" />  
        <w:lang w:val="en-US" w:eastAsia="en-US" w:bidi="ar-SA" />  
      </w:rPr>  
    </w:rPrDefault>  
    <w:pPrDefault />  
  </w:docDefaults>  
  <w:style w:type="paragraph" w:default="1" w:styleId="Normal">  
    <w:name w:val="Normal" />  
    <w:qFormat />  
    <w:rPr>  
      <w:sz w:val="24" />  
      <w:szCs w:val="24" />  
    </w:rPr>  
  </w:style>  
  <w:style w:type="paragraph" w:styleId="Heading1">  
    <w:name w:val="heading 1" />  
    <w:basedOn w:val="Normal" />  
    <w:next w:val="Normal" />  
    <w:link w:val="Heading1Char" />  
    <w:uiPriority w:val="99" />  
    <w:qFormat />  
    <w:rsid w:val="006027C7" />  
    <w:pPr>  
      <w:keepNext />  
      <w:spacing w:before="240" w:after="60" />  
      <w:outlineLvl w:val="0" />  
    </w:pPr>  
    <w:rPr>  
      <w:rFonts w:ascii="Arial" w:hAnsi="Arial" w:cs="Arial" />  
      <w:b />  
      <w:bCs />  
      <w:kern w:val="32" />  
      <w:sz w:val="32" />  
      <w:szCs w:val="32" />  
    </w:rPr>  
  </w:style>  
  <w:style w:type="character" w:default="1" w:styleId="DefaultParagraphFont">  
    <w:name w:val="Default Paragraph Font" />  
    <w:uiPriority w:val="99" />  
    <w:semiHidden />  
  </w:style>  
  <w:style w:type="table" w:default="1" w:styleId="TableNormal">  
    <w:name w:val="Normal Table" />  
    <w:uiPriority w:val="99" />  
    <w:semiHidden />  
    <w:unhideWhenUsed />  
    <w:qFormat />  
    <w:tblPr>  
      <w:tblInd w:w="0" w:type="dxa" />  
      <w:tblCellMar>  
        <w:top w:w="0" w:type="dxa" />  
        <w:left w:w="108" w:type="dxa" />  
        <w:bottom w:w="0" w:type="dxa" />  
        <w:right w:w="108" w:type="dxa" />  
      </w:tblCellMar>  
    </w:tblPr>  
  </w:style>  
  <w:style w:type="numbering" w:default="1" w:styleId="NoList">  
    <w:name w:val="No List" />  
    <w:uiPriority w:val="99" />  
    <w:semiHidden />  
    <w:unhideWhenUsed />  
  </w:style>  
  <w:style w:type="character" w:customStyle="1" w:styleId="Heading1Char">  
    <w:name w:val="Heading 1 Char" />  
    <w:basedOn w:val="DefaultParagraphFont" />  
    <w:link w:val="Heading1" />  
    <w:uiPriority w:val="9" />  
    <w:rsid w:val="009765E3" />  
    <w:rPr>  
      <w:rFonts  
          w:asciiTheme="majorHAnsi"  
          w:eastAsiaTheme="majorEastAsia"  
          w:hAnsiTheme="majorHAnsi"  
          w:cstheme="majorBidi" />  
      <w:b />  
      <w:bCs />  
      <w:kern w:val="32" />  
      <w:sz w:val="32" />  
      <w:szCs w:val="32" />  
    </w:rPr>  
  </w:style>  
  <w:style w:type="paragraph" w:customStyle="1" w:styleId="Code">  
    <w:name w:val="Code" />  
    <w:aliases w:val="c" />  
    <w:uiPriority w:val="99" />  
    <w:rsid w:val="006027C7" />  
    <w:pPr>  
      <w:spacing w:after="60" w:line="300" w:lineRule="exact" />  
    </w:pPr>  
    <w:rPr>  
      <w:rFonts w:ascii="Courier New" w:hAnsi="Courier New" />  
      <w:noProof />  
      <w:color w:val="000080" />  
      <w:sz w:val="20" />  
      <w:szCs w:val="20" />  
    </w:rPr>  
  </w:style>  
</w:styles>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e99c1-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e99c1-113">See also</span></span>

- [<span data-ttu-id="e99c1-114">Ayrıntılar Office Open XML WordprocessingML belgelerinin (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e99c1-114">Details of Office Open XML WordprocessingML Documents (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/details-of-office-open-xml-wordprocessingml-documents.md)
