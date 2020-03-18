---
title: WordprocessingML Belgesinin Stil Kısmı
ms.date: 07/20/2015
ms.assetid: 5458bccf-3898-4661-904b-7d280c9239a9
ms.openlocfilehash: 56726a7ea7594bfd1c68e5b1f8e45f585138eac6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "68868635"
---
# <a name="style-part-of-a-wordprocessingml-document"></a><span data-ttu-id="e9ec6-102">WordprocessingML Belgesinin Stil Kısmı</span><span class="sxs-lookup"><span data-stu-id="e9ec6-102">Style Part of a WordprocessingML Document</span></span>
<span data-ttu-id="e9ec6-103">Bu konu, Office Open XML WordprocessingML belgesinin stil bölümünün bir örneğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="e9ec6-103">This topic shows an example of the style part of the Office Open XML WordprocessingML document.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e9ec6-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="e9ec6-104">Example</span></span>  
 <span data-ttu-id="e9ec6-105">Aşağıdaki örnek, Office Open XML WordprocessingML belgesinin stil bölümünü oluşturan XML'dir.</span><span class="sxs-lookup"><span data-stu-id="e9ec6-105">The following example is the XML that makes up the style part of an Office Open XML WordprocessingML document.</span></span>  
  
 <span data-ttu-id="e9ec6-106">Varsayılan paragraf stilinde aşağıdaki açılış etiketine sahip bir öğe vardır:</span><span class="sxs-lookup"><span data-stu-id="e9ec6-106">The default paragraph style has an element with the following opening tag:</span></span>  
  
```xml
<w:style w:type="paragraph" w:default="1" w:styleId="Normal">  
```  
  
 <span data-ttu-id="e9ec6-107">Sorgunun varsayılan stili olan paragrafların stilini tanımlayabilmesi için varsayılan stil tanımlayıcısını bulmak için sorguyu yazarken bu bilgileri bilmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="e9ec6-107">You need to know this information when you write the query to find the default style identifier, so that the query can identify the style of paragraphs that have the default style.</span></span>  
  
 <span data-ttu-id="e9ec6-108">Microsoft Word'ün oluşturduğu tipik belgelerle karşılaştırıldığında bu belgelerin çok basit olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="e9ec6-108">Note that these documents are very simple when compared to typical documents that Microsoft Word generates.</span></span> <span data-ttu-id="e9ec6-109">Çoğu durumda, Word çok sayıda ek bilgi, ek biçimlendirme ve meta veri kaydeder.</span><span class="sxs-lookup"><span data-stu-id="e9ec6-109">In many cases, Word saves a great deal of additional information, additional formatting and metadata.</span></span> <span data-ttu-id="e9ec6-110">Ayrıca, Word satırları bu örnekte olduğu gibi kolayca okunabilecek şekilde biçimlendirmez; bunun yerine, XML girintisi olmadan kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="e9ec6-110">Furthermore, Word does not format the lines to be easily readable as in this example; instead, the XML is saved without indentation.</span></span> <span data-ttu-id="e9ec6-111">Ancak, tüm WordprocessingML belgeleri aynı temel XML şeklini paylaşır.</span><span class="sxs-lookup"><span data-stu-id="e9ec6-111">However, all WordprocessingML documents share the same basic XML shape.</span></span> <span data-ttu-id="e9ec6-112">Bu nedenle, bu öğreticide sunulan sorgular daha karmaşık belgelerle çalışır.</span><span class="sxs-lookup"><span data-stu-id="e9ec6-112">Because of this, the queries presented in this tutorial will work with more complicated documents.</span></span>  
  
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
