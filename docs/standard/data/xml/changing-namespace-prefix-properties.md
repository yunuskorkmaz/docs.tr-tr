---
title: Namespace önek özelliklerini değiştirme
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: d5c87cbe-4d69-429f-aad5-3103c2ca2770
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e3f41ba7281d67cc2ce848597926f5efebf4d489
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33568699"
---
# <a name="changing-namespace-prefix-properties"></a><span data-ttu-id="1cf1e-102">Namespace önek özelliklerini değiştirme</span><span class="sxs-lookup"><span data-stu-id="1cf1e-102">Changing Namespace Prefix Properties</span></span>
<span data-ttu-id="1cf1e-103">**XmlNode** sınıfı belirli bir düğümle ilişkilendirilen ad alanı öneki değiştirmenize izin verir.</span><span class="sxs-lookup"><span data-stu-id="1cf1e-103">The **XmlNode** class allows you to change the namespace prefix associated with a given node.</span></span> <span data-ttu-id="1cf1e-104">Örneğin, aşağıdaki kod, bir öğenin değiştirilmesini önek gösterir.</span><span class="sxs-lookup"><span data-stu-id="1cf1e-104">For example, the following code shows the prefix of an element being changed.</span></span>  
  
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
  
 <span data-ttu-id="1cf1e-105">**Output**</span><span class="sxs-lookup"><span data-stu-id="1cf1e-105">**Output**</span></span>  
  
```xml  
<b:test xmlns:a="123" xmlns:b="456" />  
```  
  
 <span data-ttu-id="1cf1e-106">Bir düğümün önek değiştirmek kendi ad değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="1cf1e-106">Changing the prefix of a node does not change its namespace.</span></span> <span data-ttu-id="1cf1e-107">Ad yalnızca düğüm oluşturulduğunda ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1cf1e-107">The namespace can only be set when the node is created.</span></span> <span data-ttu-id="1cf1e-108">Ağaç kalır, yeni ad alanı öznitelikler çıkışı ayarladığınız önek karşılamak için kalıcı.</span><span class="sxs-lookup"><span data-stu-id="1cf1e-108">When you persist the tree, new namespace attributes may be persisted out to satisfy the prefix you set.</span></span> <span data-ttu-id="1cf1e-109">Yeni ad alanı oluşturulamazsa düğüm kendi yerel ve ad alanına korur şekilde önek değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="1cf1e-109">If the new namespace cannot be created, then the prefix is changed so the node preserves its local name and namespace.</span></span> <span data-ttu-id="1cf1e-110">Aşağıdaki örnek eklenmekte olan bir ad özniteliği gösterir.</span><span class="sxs-lookup"><span data-stu-id="1cf1e-110">The following example shows a namespace attribute being added.</span></span>  
  
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
  
 <span data-ttu-id="1cf1e-111">**Output**</span><span class="sxs-lookup"><span data-stu-id="1cf1e-111">**Output**</span></span>  
  
```xml  
<a:test xmlns="123" xmlns:a="123" />  
```  
  
 <span data-ttu-id="1cf1e-112">Ne zaman ağaç kalıcı bir dizeye çağrısı sonucunda **belge. InnerXml**, `xmlns:a='123'` özniteliği ad alanını korumak için eklenmiştir `test` öğesi.</span><span class="sxs-lookup"><span data-stu-id="1cf1e-112">When the tree was persisted to a string as a result of the call to **doc.InnerXml**, the `xmlns:a='123'` attribute was added to preserve the namespace of the `test` element.</span></span> <span data-ttu-id="1cf1e-113">Bu `'123'`, ve bunu kalan `'123'`.</span><span class="sxs-lookup"><span data-stu-id="1cf1e-113">It was `'123'`, and it remained `'123'`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1cf1e-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1cf1e-114">See Also</span></span>  
 [<span data-ttu-id="1cf1e-115">XML Belge Nesne Modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="1cf1e-115">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
