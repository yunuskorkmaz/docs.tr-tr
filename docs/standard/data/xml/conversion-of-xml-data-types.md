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
ms.openlocfilehash: cec2b85c55871c8a21a74e79cfcdd041fa063bec
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43866630"
---
# <a name="conversion-of-xml-data-types"></a><span data-ttu-id="293b8-102">XML veri türlerini dönüştürme</span><span class="sxs-lookup"><span data-stu-id="293b8-102">Conversion of XML Data Types</span></span>
<span data-ttu-id="293b8-103">Yöntemlerin çoğunun bulunan bir **XmlConvert** sınıfı veri dizeler ve kesin tür belirtilmiş biçimleri arasında dönüştürmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="293b8-103">The majority of the methods found in an **XmlConvert** class are used to convert data between strings and strongly-typed formats.</span></span> <span data-ttu-id="293b8-104">Yerel ayar bağımsız yöntemlerdir.</span><span class="sxs-lookup"><span data-stu-id="293b8-104">Methods are locale independent.</span></span> <span data-ttu-id="293b8-105">Bu, tüm yerel ayarlar dönüştürme yaparken dikkate değil, anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="293b8-105">This means that they do not take into account any locale settings when doing conversion.</span></span>  
  
## <a name="reading-string-as-types"></a><span data-ttu-id="293b8-106">Okuma dize türleri olarak</span><span class="sxs-lookup"><span data-stu-id="293b8-106">Reading String as types</span></span>  
 <span data-ttu-id="293b8-107">Aşağıdaki örnek bir dize olarak okur ve ona dönüştürür bir **DateTime** türü.</span><span class="sxs-lookup"><span data-stu-id="293b8-107">The following sample reads a string and converts it to a **DateTime** type.</span></span>  
  
 <span data-ttu-id="293b8-108">Aşağıdaki XML geçirmesini:</span><span class="sxs-lookup"><span data-stu-id="293b8-108">Given the following XML input:</span></span>  
  
 <span data-ttu-id="293b8-109">**Giriş**</span><span class="sxs-lookup"><span data-stu-id="293b8-109">**Input**</span></span>  
  
```xml  
<Element>2001-02-27T11:13:23</Element>  
```  
  
 <span data-ttu-id="293b8-110">Bu kod dizeye dönüştürür **DateTime** biçimi:</span><span class="sxs-lookup"><span data-stu-id="293b8-110">This code converts the string to the **DateTime** format:</span></span>  
  
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
  
## <a name="writing-strings-as-types"></a><span data-ttu-id="293b8-111">Yazma dize türleri olarak</span><span class="sxs-lookup"><span data-stu-id="293b8-111">Writing Strings as types</span></span>  
 <span data-ttu-id="293b8-112">Aşağıdaki örnek okuma bir **Int32** ve bir dizeye dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="293b8-112">The following sample reads an **Int32** and converts it to a string.</span></span>  
  
 <span data-ttu-id="293b8-113">Aşağıdaki XML geçirmesini:</span><span class="sxs-lookup"><span data-stu-id="293b8-113">Given the following XML input:</span></span>  
  
 <span data-ttu-id="293b8-114">**Giriş**</span><span class="sxs-lookup"><span data-stu-id="293b8-114">**Input**</span></span>  
  
```xml  
<TestInt32>-2147483648</TestInt32>  
```  
  
 <span data-ttu-id="293b8-115">Bu kod dönüştürür **Int32** içine bir **dize**:</span><span class="sxs-lookup"><span data-stu-id="293b8-115">This code converts the **Int32** into a **String**:</span></span>  
  
```vb  
Dim vInt32 As Int32 = -2147483648  
writer.WriteElementString("TestInt32", XmlConvert.ToString(vInt32))  
```  
  
```csharp  
Int32 vInt32=-2147483648;  
writer.WriteElementString("TestInt32",XmlConvert.ToString(vInt32));  
```  
  
## <a name="see-also"></a><span data-ttu-id="293b8-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="293b8-116">See also</span></span>

- [<span data-ttu-id="293b8-117">.NET Framework Veri Türleri için Dizeleri Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="293b8-117">Converting Strings to .NET Framework Data Types</span></span>](../../../../docs/standard/data/xml/converting-strings-to-dotnet-data-types.md)  
- [<span data-ttu-id="293b8-118">.NET Framework Türlerini Dizelere Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="293b8-118">Converting .NET Framework Types to Strings</span></span>](../../../../docs/standard/data/xml/converting-dotnet-types-to-strings.md)
