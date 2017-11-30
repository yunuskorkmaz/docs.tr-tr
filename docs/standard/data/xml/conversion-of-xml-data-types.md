---
title: "XML veri türlerini dönüştürme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: a2aa99ba-8239-4818-9281-f1d72ee40bde
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d2f5f5d27b3d21ff12f5eea7613e80e73c5b6597
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="conversion-of-xml-data-types"></a><span data-ttu-id="d70e2-102">XML veri türlerini dönüştürme</span><span class="sxs-lookup"><span data-stu-id="d70e2-102">Conversion of XML Data Types</span></span>
<span data-ttu-id="d70e2-103">Yöntemleri çoğunluğu bulunan bir **XmlConvert** sınıfı, dizeleri ve kesin türü belirtilmiş biçimleri arasında veri dönüştürmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d70e2-103">The majority of the methods found in an **XmlConvert** class are used to convert data between strings and strongly-typed formats.</span></span> <span data-ttu-id="d70e2-104">Yerel ayar bağımsız yöntemleridir.</span><span class="sxs-lookup"><span data-stu-id="d70e2-104">Methods are locale independent.</span></span> <span data-ttu-id="d70e2-105">Bu, bunlar herhangi bir yerel ayarı dönüştürme yapılırken dikkate değil, anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="d70e2-105">This means that they do not take into account any locale settings when doing conversion.</span></span>  
  
## <a name="reading-string-as-types"></a><span data-ttu-id="d70e2-106">Okuma dize türleri olarak</span><span class="sxs-lookup"><span data-stu-id="d70e2-106">Reading String as types</span></span>  
 <span data-ttu-id="d70e2-107">Aşağıdaki örnek bir dize okur ve ona dönüştüren bir **DateTime** türü.</span><span class="sxs-lookup"><span data-stu-id="d70e2-107">The following sample reads a string and converts it to a **DateTime** type.</span></span>  
  
 <span data-ttu-id="d70e2-108">Aşağıdaki XML giriş verilen:</span><span class="sxs-lookup"><span data-stu-id="d70e2-108">Given the following XML input:</span></span>  
  
 <span data-ttu-id="d70e2-109">**Giriş**</span><span class="sxs-lookup"><span data-stu-id="d70e2-109">**Input**</span></span>  
  
```xml  
<Element>2001-02-27T11:13:23</Element>  
```  
  
 <span data-ttu-id="d70e2-110">Bu kod dizeye dönüştürür **DateTime** biçimi:</span><span class="sxs-lookup"><span data-stu-id="d70e2-110">This code converts the string to the **DateTime** format:</span></span>  
  
```vb  
reader.ReadStartElement()  
Dim vDateTime As DateTime = XmlConvert.ToDateTime(reader.ReadString())  
Console.WriteLine(vDateTime)  
```  
  
```csharp  
reader.ReadStartElement();  
DateTime vDateTime = XmlConvert.ToDateTime(reader.ReadString());  
Console.WriteLine(vDateTime);  
```  
  
## <a name="writing-strings-as-types"></a><span data-ttu-id="d70e2-111">Yazma dize türleri olarak</span><span class="sxs-lookup"><span data-stu-id="d70e2-111">Writing Strings as types</span></span>  
 <span data-ttu-id="d70e2-112">Aşağıdaki örnek okuma bir **Int32** ve bir dizeye dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="d70e2-112">The following sample reads an **Int32** and converts it to a string.</span></span>  
  
 <span data-ttu-id="d70e2-113">Aşağıdaki XML giriş verilen:</span><span class="sxs-lookup"><span data-stu-id="d70e2-113">Given the following XML input:</span></span>  
  
 <span data-ttu-id="d70e2-114">**Giriş**</span><span class="sxs-lookup"><span data-stu-id="d70e2-114">**Input**</span></span>  
  
```xml  
<TestInt32>-2147483648</TestInt32>  
```  
  
 <span data-ttu-id="d70e2-115">Bu kod dönüştürür **Int32** içine bir **dize**:</span><span class="sxs-lookup"><span data-stu-id="d70e2-115">This code converts the **Int32** into a **String**:</span></span>  
  
```vb  
Dim vInt32 As Int32 = -2147483648  
writer.WriteElementString("TestInt32", XmlConvert.ToString(vInt32))  
```  
  
```csharp  
Int32 vInt32=-2147483648;  
writer.WriteElementString("TestInt32",XmlConvert.ToString(vInt32));  
```  
  
## <a name="see-also"></a><span data-ttu-id="d70e2-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d70e2-116">See Also</span></span>  
 [<span data-ttu-id="d70e2-117">.NET Framework veri türleri için dizeleri dönüştürme</span><span class="sxs-lookup"><span data-stu-id="d70e2-117">Converting Strings to .NET Framework Data Types</span></span>](../../../../docs/standard/data/xml/converting-strings-to-dotnet-data-types.md)  
 [<span data-ttu-id="d70e2-118">.NET Framework türleri dizeleri dönüştürme</span><span class="sxs-lookup"><span data-stu-id="d70e2-118">Converting .NET Framework Types to Strings</span></span>](../../../../docs/standard/data/xml/converting-dotnet-types-to-strings.md)
