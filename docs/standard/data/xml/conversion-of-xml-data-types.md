---
title: XML veri türlerini dönüştürme
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: a2aa99ba-8239-4818-9281-f1d72ee40bde
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 56b5b51848858b7f1240059ca30eb48474650b73
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54555134"
---
# <a name="conversion-of-xml-data-types"></a><span data-ttu-id="eeb5b-102">XML veri türlerini dönüştürme</span><span class="sxs-lookup"><span data-stu-id="eeb5b-102">Conversion of XML Data Types</span></span>
<span data-ttu-id="eeb5b-103">Yöntemlerin çoğunun bulunan bir **XmlConvert** sınıfı veri dizeler ve kesin tür belirtilmiş biçimleri arasında dönüştürmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="eeb5b-103">The majority of the methods found in an **XmlConvert** class are used to convert data between strings and strongly-typed formats.</span></span> <span data-ttu-id="eeb5b-104">Yerel ayar bağımsız yöntemlerdir.</span><span class="sxs-lookup"><span data-stu-id="eeb5b-104">Methods are locale independent.</span></span> <span data-ttu-id="eeb5b-105">Bu, tüm yerel ayarlar dönüştürme yaparken dikkate değil, anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="eeb5b-105">This means that they do not take into account any locale settings when doing conversion.</span></span>  
  
## <a name="reading-string-as-types"></a><span data-ttu-id="eeb5b-106">Okuma dize türleri olarak</span><span class="sxs-lookup"><span data-stu-id="eeb5b-106">Reading String as types</span></span>  
 <span data-ttu-id="eeb5b-107">Aşağıdaki örnek bir dize olarak okur ve ona dönüştürür bir **DateTime** türü.</span><span class="sxs-lookup"><span data-stu-id="eeb5b-107">The following sample reads a string and converts it to a **DateTime** type.</span></span>  
  
 <span data-ttu-id="eeb5b-108">Aşağıdaki XML geçirmesini:</span><span class="sxs-lookup"><span data-stu-id="eeb5b-108">Given the following XML input:</span></span>  
  
 <span data-ttu-id="eeb5b-109">**Giriş**</span><span class="sxs-lookup"><span data-stu-id="eeb5b-109">**Input**</span></span>  
  
```xml  
<Element>2001-02-27T11:13:23</Element>  
```  
  
 <span data-ttu-id="eeb5b-110">Bu kod dizeye dönüştürür **DateTime** biçimi:</span><span class="sxs-lookup"><span data-stu-id="eeb5b-110">This code converts the string to the **DateTime** format:</span></span>  
  
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
  
## <a name="writing-strings-as-types"></a><span data-ttu-id="eeb5b-111">Yazma dize türleri olarak</span><span class="sxs-lookup"><span data-stu-id="eeb5b-111">Writing Strings as types</span></span>  
 <span data-ttu-id="eeb5b-112">Aşağıdaki örnek okuma bir **Int32** ve bir dizeye dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="eeb5b-112">The following sample reads an **Int32** and converts it to a string.</span></span>  
  
 <span data-ttu-id="eeb5b-113">Aşağıdaki XML geçirmesini:</span><span class="sxs-lookup"><span data-stu-id="eeb5b-113">Given the following XML input:</span></span>  
  
 <span data-ttu-id="eeb5b-114">**Giriş**</span><span class="sxs-lookup"><span data-stu-id="eeb5b-114">**Input**</span></span>  
  
```xml  
<TestInt32>-2147483648</TestInt32>  
```  
  
 <span data-ttu-id="eeb5b-115">Bu kod dönüştürür **Int32** içine bir **dize**:</span><span class="sxs-lookup"><span data-stu-id="eeb5b-115">This code converts the **Int32** into a **String**:</span></span>  
  
```vb  
Dim vInt32 As Int32 = -2147483648  
writer.WriteElementString("TestInt32", XmlConvert.ToString(vInt32))  
```  
  
```csharp  
Int32 vInt32=-2147483648;  
writer.WriteElementString("TestInt32",XmlConvert.ToString(vInt32));  
```  
  
## <a name="see-also"></a><span data-ttu-id="eeb5b-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eeb5b-116">See also</span></span>

- [<span data-ttu-id="eeb5b-117">.NET Framework Veri Türleri için Dizeleri Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="eeb5b-117">Converting Strings to .NET Framework Data Types</span></span>](../../../../docs/standard/data/xml/converting-strings-to-dotnet-data-types.md)
- [<span data-ttu-id="eeb5b-118">.NET Framework Türlerini Dizelere Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="eeb5b-118">Converting .NET Framework Types to Strings</span></span>](../../../../docs/standard/data/xml/converting-dotnet-types-to-strings.md)
