---
description: 'Daha fazla bilgi edinin: ad alanı öneki özelliklerini değiştirme'
title: Ad Alanı Ön Ek Özelliklerini Değiştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d5c87cbe-4d69-429f-aad5-3103c2ca2770
ms.openlocfilehash: f6ca7d1c732f357a2c3ff8ba847d65314da81083
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99714007"
---
# <a name="changing-namespace-prefix-properties"></a><span data-ttu-id="f6958-103">Ad Alanı Ön Ek Özelliklerini Değiştirme</span><span class="sxs-lookup"><span data-stu-id="f6958-103">Changing Namespace Prefix Properties</span></span>

<span data-ttu-id="f6958-104">**XMLNode** sınıfı, belirli bir düğümle ilişkili ad alanı önekini değiştirmenize izin verir.</span><span class="sxs-lookup"><span data-stu-id="f6958-104">The **XmlNode** class allows you to change the namespace prefix associated with a given node.</span></span> <span data-ttu-id="f6958-105">Örneğin, aşağıdaki kod değiştirilmekte olan bir öğenin önekini gösterir.</span><span class="sxs-lookup"><span data-stu-id="f6958-105">For example, the following code shows the prefix of an element being changed.</span></span>  
  
```vb  
Dim doc as XmlDocument = new XmlDocument()  
doc.LoadXml("<a:test xmlns:a='123' xmlns:b='456'/>")  
Dim e as XmlElement = doc.DocumentElement  
e.Prefix = "b"  
Console.WriteLine(doc.InnerXml)  
```  
  
```csharp  
XmlDocument doc = new XmlDocument();  
doc.LoadXml("<a:test xmlns:a='123' xmlns:b='456'/>");  
XmlElement e = doc.DocumentElement;
e.Prefix = "b";  
Console.WriteLine(doc.InnerXml);  
```  
  
 <span data-ttu-id="f6958-106">**Çıktı**</span><span class="sxs-lookup"><span data-stu-id="f6958-106">**Output**</span></span>  
  
```xml  
<b:test xmlns:a="123" xmlns:b="456" />  
```  
  
 <span data-ttu-id="f6958-107">Bir düğümün önekini değiştirmek, ad alanını değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="f6958-107">Changing the prefix of a node does not change its namespace.</span></span> <span data-ttu-id="f6958-108">Ad alanı yalnızca düğüm oluşturulduğunda ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="f6958-108">The namespace can only be set when the node is created.</span></span> <span data-ttu-id="f6958-109">Ağacı kalıcı hale getirdikten sonra, ayarladığınız ön eki karşılamak için yeni ad alanı öznitelikleri kalıcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="f6958-109">When you persist the tree, new namespace attributes may be persisted out to satisfy the prefix you set.</span></span> <span data-ttu-id="f6958-110">Yeni ad alanı oluşturuoluşturulamadığı takdirde, düğüm yerel adını ve ad alanını koruyabilmesi için önek değişir.</span><span class="sxs-lookup"><span data-stu-id="f6958-110">If the new namespace cannot be created, then the prefix is changed so the node preserves its local name and namespace.</span></span> <span data-ttu-id="f6958-111">Aşağıdaki örnekte, eklenmekte olan bir ad alanı özniteliği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f6958-111">The following example shows a namespace attribute being added.</span></span>  
  
```vb  
Dim doc as XmlDocument = new XmlDocument()  
doc.LoadXml("<test xmlns='123'/>")  
Dim e as XmlElement = doc.DocumentElement  
e.Prefix = "a"  
Console.WriteLine(doc.InnerXml)  
```  
  
```csharp  
XmlDocument doc = new XmlDocument();  
doc.LoadXml("<test xmlns='123'/>");  
XmlElement e = doc.DocumentElement;
e.Prefix = "a";  
Console.WriteLine(doc.InnerXml);  
```  
  
 <span data-ttu-id="f6958-112">**Çıktı**</span><span class="sxs-lookup"><span data-stu-id="f6958-112">**Output**</span></span>  
  
```xml  
<a:test xmlns="123" xmlns:a="123" />  
```  
  
 <span data-ttu-id="f6958-113">Ağaç, belge çağrısının bir sonucu olarak bir dizeye kalıcı yapıldığında **. InnerXml**, `xmlns:a='123'` öğesinin ad alanını korumak için eklenmiştir `test` .</span><span class="sxs-lookup"><span data-stu-id="f6958-113">When the tree was persisted to a string as a result of the call to **doc.InnerXml**, the `xmlns:a='123'` attribute was added to preserve the namespace of the `test` element.</span></span> <span data-ttu-id="f6958-114">İdi `'123'` ve kaldı `'123'` .</span><span class="sxs-lookup"><span data-stu-id="f6958-114">It was `'123'`, and it remained `'123'`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6958-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f6958-115">See also</span></span>

- [<span data-ttu-id="f6958-116">XML Belge Nesne Modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="f6958-116">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
