---
description: 'Daha fazla bilgi edinin: XML veri türlerini dönüştürme'
title: XML Veri Türlerini Dönüştürme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a2aa99ba-8239-4818-9281-f1d72ee40bde
ms.openlocfilehash: 7f7657f3ee290ff88dff1ef869a723c947cbce5f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99713955"
---
# <a name="conversion-of-xml-data-types"></a><span data-ttu-id="a18d5-103">XML Veri Türlerini Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="a18d5-103">Conversion of XML Data Types</span></span>

<span data-ttu-id="a18d5-104">**XmlConvert** sınıfında bulunan yöntemlerin çoğu, dizeleri ve kesin belirlenmiş biçimleri arasında veri dönüştürmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a18d5-104">The majority of the methods found in an **XmlConvert** class are used to convert data between strings and strongly typed formats.</span></span> <span data-ttu-id="a18d5-105">Yöntemler yerel olarak bağımsızdır.</span><span class="sxs-lookup"><span data-stu-id="a18d5-105">Methods are locale independent.</span></span> <span data-ttu-id="a18d5-106">Bu, dönüştürme yaparken herhangi bir yerel ayarı dikkate almaz demektir.</span><span class="sxs-lookup"><span data-stu-id="a18d5-106">This means that they do not take into account any locale settings when doing conversion.</span></span>  
  
## <a name="reading-string-as-types"></a><span data-ttu-id="a18d5-107">Dize tür olarak okunuyor</span><span class="sxs-lookup"><span data-stu-id="a18d5-107">Reading String as types</span></span>  

 <span data-ttu-id="a18d5-108">Aşağıdaki örnek bir dize okur ve bunu bir **Tarih saat** türüne dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="a18d5-108">The following sample reads a string and converts it to a **DateTime** type.</span></span>  
  
 <span data-ttu-id="a18d5-109">Aşağıdaki XML girişi verildi:</span><span class="sxs-lookup"><span data-stu-id="a18d5-109">Given the following XML input:</span></span>  
  
 <span data-ttu-id="a18d5-110">**Giriş**</span><span class="sxs-lookup"><span data-stu-id="a18d5-110">**Input**</span></span>  
  
```xml  
<Element>2001-02-27T11:13:23</Element>  
```  
  
 <span data-ttu-id="a18d5-111">Bu kod, dizeyi **Tarih saat** biçimine dönüştürür:</span><span class="sxs-lookup"><span data-stu-id="a18d5-111">This code converts the string to the **DateTime** format:</span></span>  
  
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
  
## <a name="writing-strings-as-types"></a><span data-ttu-id="a18d5-112">Dizeleri tür olarak yazma</span><span class="sxs-lookup"><span data-stu-id="a18d5-112">Writing Strings as types</span></span>  

 <span data-ttu-id="a18d5-113">Aşağıdaki örnek bir **Int32** okur ve bunu bir dizeye dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="a18d5-113">The following sample reads an **Int32** and converts it to a string.</span></span>  
  
 <span data-ttu-id="a18d5-114">Aşağıdaki XML girişi verildi:</span><span class="sxs-lookup"><span data-stu-id="a18d5-114">Given the following XML input:</span></span>  
  
 <span data-ttu-id="a18d5-115">**Giriş**</span><span class="sxs-lookup"><span data-stu-id="a18d5-115">**Input**</span></span>  
  
```xml  
<TestInt32>-2147483648</TestInt32>  
```  
  
 <span data-ttu-id="a18d5-116">Bu kod, **Int32** 'Yi bir **dizeye** dönüştürür:</span><span class="sxs-lookup"><span data-stu-id="a18d5-116">This code converts the **Int32** into a **String**:</span></span>  
  
```vb  
Dim vInt32 As Int32 = -2147483648  
writer.WriteElementString("TestInt32", XmlConvert.ToString(vInt32))  
```  
  
```csharp  
Int32 vInt32=-2147483648;  
writer.WriteElementString("TestInt32",XmlConvert.ToString(vInt32));  
```  
  
## <a name="see-also"></a><span data-ttu-id="a18d5-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a18d5-117">See also</span></span>

- [<span data-ttu-id="a18d5-118">.NET Framework Veri Türleri için Dizeleri Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="a18d5-118">Converting Strings to .NET Framework Data Types</span></span>](converting-strings-to-dotnet-data-types.md)
- [<span data-ttu-id="a18d5-119">.NET Framework Türlerini Dizelere Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="a18d5-119">Converting .NET Framework Types to Strings</span></span>](converting-dotnet-types-to-strings.md)
