---
title: XML Veri Türlerini Dönüştürme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a2aa99ba-8239-4818-9281-f1d72ee40bde
ms.openlocfilehash: d7ee7447ab7a8be1bad0d087dba5fc2afaa878e8
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94830980"
---
# <a name="conversion-of-xml-data-types"></a><span data-ttu-id="84eca-102">XML Veri Türlerini Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="84eca-102">Conversion of XML Data Types</span></span>
<span data-ttu-id="84eca-103">**XmlConvert** sınıfında bulunan yöntemlerin çoğu, dizeleri ve kesin belirlenmiş biçimleri arasında veri dönüştürmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="84eca-103">The majority of the methods found in an **XmlConvert** class are used to convert data between strings and strongly typed formats.</span></span> <span data-ttu-id="84eca-104">Yöntemler yerel olarak bağımsızdır.</span><span class="sxs-lookup"><span data-stu-id="84eca-104">Methods are locale independent.</span></span> <span data-ttu-id="84eca-105">Bu, dönüştürme yaparken herhangi bir yerel ayarı dikkate almaz demektir.</span><span class="sxs-lookup"><span data-stu-id="84eca-105">This means that they do not take into account any locale settings when doing conversion.</span></span>  
  
## <a name="reading-string-as-types"></a><span data-ttu-id="84eca-106">Dize tür olarak okunuyor</span><span class="sxs-lookup"><span data-stu-id="84eca-106">Reading String as types</span></span>  
 <span data-ttu-id="84eca-107">Aşağıdaki örnek bir dize okur ve bunu bir **Tarih saat** türüne dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="84eca-107">The following sample reads a string and converts it to a **DateTime** type.</span></span>  
  
 <span data-ttu-id="84eca-108">Aşağıdaki XML girişi verildi:</span><span class="sxs-lookup"><span data-stu-id="84eca-108">Given the following XML input:</span></span>  
  
 <span data-ttu-id="84eca-109">**Giriş**</span><span class="sxs-lookup"><span data-stu-id="84eca-109">**Input**</span></span>  
  
```xml  
<Element>2001-02-27T11:13:23</Element>  
```  
  
 <span data-ttu-id="84eca-110">Bu kod, dizeyi **Tarih saat** biçimine dönüştürür:</span><span class="sxs-lookup"><span data-stu-id="84eca-110">This code converts the string to the **DateTime** format:</span></span>  
  
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
  
## <a name="writing-strings-as-types"></a><span data-ttu-id="84eca-111">Dizeleri tür olarak yazma</span><span class="sxs-lookup"><span data-stu-id="84eca-111">Writing Strings as types</span></span>  
 <span data-ttu-id="84eca-112">Aşağıdaki örnek bir **Int32** okur ve bunu bir dizeye dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="84eca-112">The following sample reads an **Int32** and converts it to a string.</span></span>  
  
 <span data-ttu-id="84eca-113">Aşağıdaki XML girişi verildi:</span><span class="sxs-lookup"><span data-stu-id="84eca-113">Given the following XML input:</span></span>  
  
 <span data-ttu-id="84eca-114">**Giriş**</span><span class="sxs-lookup"><span data-stu-id="84eca-114">**Input**</span></span>  
  
```xml  
<TestInt32>-2147483648</TestInt32>  
```  
  
 <span data-ttu-id="84eca-115">Bu kod, **Int32** 'Yi bir **dizeye** dönüştürür:</span><span class="sxs-lookup"><span data-stu-id="84eca-115">This code converts the **Int32** into a **String**:</span></span>  
  
```vb  
Dim vInt32 As Int32 = -2147483648  
writer.WriteElementString("TestInt32", XmlConvert.ToString(vInt32))  
```  
  
```csharp  
Int32 vInt32=-2147483648;  
writer.WriteElementString("TestInt32",XmlConvert.ToString(vInt32));  
```  
  
## <a name="see-also"></a><span data-ttu-id="84eca-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="84eca-116">See also</span></span>

- [<span data-ttu-id="84eca-117">.NET Framework Veri Türleri için Dizeleri Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="84eca-117">Converting Strings to .NET Framework Data Types</span></span>](converting-strings-to-dotnet-data-types.md)
- [<span data-ttu-id="84eca-118">.NET Framework Türlerini Dizelere Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="84eca-118">Converting .NET Framework Types to Strings</span></span>](converting-dotnet-types-to-strings.md)
