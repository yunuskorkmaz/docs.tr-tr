---
title: While Serializing3 boşluk koruma
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.topic: article
ms.assetid: 0c4f8b98-483b-4cf8-86be-fa146eef90dc
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: a73c4ec01c1a4d2cebe71ae1afdcce0466762c9c
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="preserving-white-space-while-serializing"></a><span data-ttu-id="3f293-102">Beyaz alan Serileştirirken koruma</span><span class="sxs-lookup"><span data-stu-id="3f293-102">Preserving White Space While Serializing</span></span>
<span data-ttu-id="3f293-103">Bu konuda, bir XML ağacı serileştirilirken boşluk denetlemek açıklar.</span><span class="sxs-lookup"><span data-stu-id="3f293-103">This topic describes how to control white space when serializing an XML tree.</span></span>  
  
 <span data-ttu-id="3f293-104">Girintili XML okuma, bir bellek içi XML ağacı boşluk metin düğüm (diğer bir deyişle, değil koruma boşluk) olmadan oluşturmak, XML bazı işlemleri ve ardından XML girintileme ile kaydetmek için yaygın bir senaryo değil.</span><span class="sxs-lookup"><span data-stu-id="3f293-104">A common scenario is to read indented XML, create an in-memory XML tree without any white-space text nodes (that is, not preserving white space), perform some operations on the XML, and then save the XML with indentation.</span></span> <span data-ttu-id="3f293-105">Biçimlendirmeye sahip XML serileştirme, yalnızca önemli boşluk XML ağacında korunur.</span><span class="sxs-lookup"><span data-stu-id="3f293-105">When you serialize the XML with formatting, only significant white space in the XML tree is preserved.</span></span> <span data-ttu-id="3f293-106">Varsayılan davranışı budur [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3f293-106">This is the default behavior for [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>  
  
 <span data-ttu-id="3f293-107">Okumak ve özellikle girintili zaten XML değiştirmek için başka bir yaygın bir senaryo değil.</span><span class="sxs-lookup"><span data-stu-id="3f293-107">Another common scenario is to read and modify XML that has already been intentionally indented.</span></span> <span data-ttu-id="3f293-108">Bu girinti herhangi bir şekilde değiştirmek istemeyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3f293-108">You might not want to change this indentation in any way.</span></span> <span data-ttu-id="3f293-109">Bunu yapmak için [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], yükleme veya XML Ayrıştırma ve XML serileştirme zaman biçimlendirme devre dışı olduğunda boşluk korumak.</span><span class="sxs-lookup"><span data-stu-id="3f293-109">To do this in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you preserve white space when you load or parse the XML and disable formatting when you serialize the XML.</span></span>  
  
## <a name="white-space-behavior-of-methods-that-serialize-xml-trees"></a><span data-ttu-id="3f293-110">Boşluk davranışı XML ağaçları Serialize yöntemi</span><span class="sxs-lookup"><span data-stu-id="3f293-110">White-Space Behavior of Methods that Serialize XML Trees</span></span>  
 <span data-ttu-id="3f293-111">Aşağıdaki yöntemleri <xref:System.Xml.Linq.XElement> ve <xref:System.Xml.Linq.XDocument> sınıfları seri bir XML ağacı.</span><span class="sxs-lookup"><span data-stu-id="3f293-111">The following methods in the <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XDocument> classes serialize an XML tree.</span></span> <span data-ttu-id="3f293-112">Bir dosyayı bir XML ağaca serileştirebiliyorsa bir <xref:System.IO.TextReader>, veya bir <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="3f293-112">You can serialize an XML tree to a file, a <xref:System.IO.TextReader>, or an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="3f293-113">`ToString` Yöntemi serileştiren bir dize.</span><span class="sxs-lookup"><span data-stu-id="3f293-113">The `ToString` method serializes to a string.</span></span>  
  
-   <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Linq.XElement.ToString%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Linq.XDocument.ToString%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="3f293-114">Yöntem değil izlerseniz <xref:System.Xml.Linq.SaveOptions> bağımsız değişken olarak, ardından yöntemi biçimlendirir (Girinti) serileştirilmiş XML.</span><span class="sxs-lookup"><span data-stu-id="3f293-114">If the method does not take <xref:System.Xml.Linq.SaveOptions> as an argument, then the method will format (indent) the serialized XML.</span></span> <span data-ttu-id="3f293-115">Bu durumda, tüm anlamsız boşluk XML ağacında göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="3f293-115">In this case, all insignificant white space in the XML tree is discarded.</span></span>  
  
 <span data-ttu-id="3f293-116">Yöntem izlerseniz <xref:System.Xml.Linq.SaveOptions> bağımsız değişken olarak, ardından yöntemi biçimlendirme olduğunu belirleyebilirsiniz (Girinti) serileştirilmiş XML.</span><span class="sxs-lookup"><span data-stu-id="3f293-116">If the method does take <xref:System.Xml.Linq.SaveOptions> as an argument, then you can specify that the method not format (indent) the serialized XML.</span></span> <span data-ttu-id="3f293-117">Bu durumda, tüm boşluk XML ağacında korunur.</span><span class="sxs-lookup"><span data-stu-id="3f293-117">In this case, all white space in the XML tree is preserved.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f293-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3f293-118">See Also</span></span>  
 [<span data-ttu-id="3f293-119">Biçimlendiricisi XML ağaçları (C#)</span><span class="sxs-lookup"><span data-stu-id="3f293-119">Serializing XML Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/serializing-xml-trees.md)
