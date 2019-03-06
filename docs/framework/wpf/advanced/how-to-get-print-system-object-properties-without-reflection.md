---
title: 'Nasıl yapılır: Yazdırma Sistemi Nesnesi Özelliklerini Yansıma Olmadan Alma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PrintSystemObject [WPF], getting properties
ms.assetid: 43560f28-183d-41c1-b9d1-de7c2552273e
ms.openlocfilehash: b03be30422a93980ecdbcdbd428600fd41abd824
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57367589"
---
# <a name="how-to-get-print-system-object-properties-without-reflection"></a><span data-ttu-id="bba3b-102">Nasıl yapılır: Yazdırma Sistemi Nesnesi Özelliklerini Yansıma Olmadan Alma</span><span class="sxs-lookup"><span data-stu-id="bba3b-102">How to: Get Print System Object Properties Without Reflection</span></span>
<span data-ttu-id="bba3b-103">Bir nesne üzerinde özelliklerini (ve bu özelliklerin türleri) belirtmek için yansıma kullanarak uygulama performansını düşürebilir.</span><span class="sxs-lookup"><span data-stu-id="bba3b-103">Using reflection to itemize the properties (and the types of those properties) on an object can slow application performance.</span></span> <span data-ttu-id="bba3b-104"><xref:System.Printing.IndexedProperties> Ad alanı, yansıma kullanarak bu bilgileri almak için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="bba3b-104">The <xref:System.Printing.IndexedProperties> namespace provides a means to getting this information with using reflection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bba3b-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="bba3b-105">Example</span></span>  
 <span data-ttu-id="bba3b-106">Bunu yapmak için adımlar aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="bba3b-106">The steps for doing this are as follows.</span></span>  
  
1.  <span data-ttu-id="bba3b-107">Türün bir örneğini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="bba3b-107">Create an instance of the type.</span></span> <span data-ttu-id="bba3b-108">Aşağıdaki örnekte türüdür <xref:System.Printing.PrintQueue> iş öğesinden türetilen türler için Microsoft .NET Framework, ancak neredeyse aynı kod ile birlikte gelen türü <xref:System.Printing.PrintSystemObject>.</span><span class="sxs-lookup"><span data-stu-id="bba3b-108">In the example below, the type is the <xref:System.Printing.PrintQueue> type that ships with Microsoft .NET Framework, but nearly identical code should work for types that you derive from <xref:System.Printing.PrintSystemObject>.</span></span>  
  
2.  <span data-ttu-id="bba3b-109">Oluşturma bir <xref:System.Printing.IndexedProperties.PrintPropertyDictionary> türün gelen <xref:System.Printing.PrintSystemObject.PropertiesCollection%2A>.</span><span class="sxs-lookup"><span data-stu-id="bba3b-109">Create a <xref:System.Printing.IndexedProperties.PrintPropertyDictionary> from the type's <xref:System.Printing.PrintSystemObject.PropertiesCollection%2A>.</span></span> <span data-ttu-id="bba3b-110"><xref:System.Collections.DictionaryEntry.Value%2A> Türlerinden türetilmiş bir nesnenin Bu sözlük her giriş özelliğidir <xref:System.Printing.IndexedProperties.PrintProperty>.</span><span class="sxs-lookup"><span data-stu-id="bba3b-110">The <xref:System.Collections.DictionaryEntry.Value%2A> property of each entry in this dictionary is an object of one of the types derived from <xref:System.Printing.IndexedProperties.PrintProperty>.</span></span>  
  
3.  <span data-ttu-id="bba3b-111">Sözlük üyelerini sıralar.</span><span class="sxs-lookup"><span data-stu-id="bba3b-111">Enumerate the members of the dictionary.</span></span> <span data-ttu-id="bba3b-112">Bunların her biri için aşağıdakileri yapın.</span><span class="sxs-lookup"><span data-stu-id="bba3b-112">For each of them, do the following.</span></span>  
  
4.  <span data-ttu-id="bba3b-113">Her giriş için değerini yukarı atama <xref:System.Printing.IndexedProperties.PrintProperty> ve oluşturmak için kullanmak bir <xref:System.Printing.IndexedProperties.PrintProperty> nesne.</span><span class="sxs-lookup"><span data-stu-id="bba3b-113">Up-cast the value of each entry to <xref:System.Printing.IndexedProperties.PrintProperty> and use it to create a <xref:System.Printing.IndexedProperties.PrintProperty> object.</span></span>  
  
5.  <span data-ttu-id="bba3b-114">Türü alma <xref:System.Printing.IndexedProperties.PrintProperty.Value%2A> her birinin <xref:System.Printing.IndexedProperties.PrintProperty> nesne.</span><span class="sxs-lookup"><span data-stu-id="bba3b-114">Get the type of the <xref:System.Printing.IndexedProperties.PrintProperty.Value%2A> of each of the <xref:System.Printing.IndexedProperties.PrintProperty> object.</span></span>  
  
 [!code-csharp[GetPrintObjectPropertyTypesWithoutReflection#ShowPropertyTypesWithoutReflection](~/samples/snippets/csharp/VS_Snippets_Wpf/GetPrintObjectPropertyTypesWithoutReflection/CSharp/Program.cs#showpropertytypeswithoutreflection)]
 [!code-vb[GetPrintObjectPropertyTypesWithoutReflection#ShowPropertyTypesWithoutReflection](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GetPrintObjectPropertyTypesWithoutReflection/visualbasic/program.vb#showpropertytypeswithoutreflection)]  
  
## <a name="see-also"></a><span data-ttu-id="bba3b-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bba3b-115">See also</span></span>
- <xref:System.Printing.IndexedProperties.PrintProperty>
- <xref:System.Printing.PrintSystemObject>
- <xref:System.Printing.IndexedProperties>
- <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>
- <xref:System.Printing.LocalPrintServer>
- <xref:System.Printing.PrintQueue>
- <xref:System.Collections.DictionaryEntry>
- [<span data-ttu-id="bba3b-116">WPF'deki Belgeler</span><span class="sxs-lookup"><span data-stu-id="bba3b-116">Documents in WPF</span></span>](documents-in-wpf.md)
- [<span data-ttu-id="bba3b-117">Yazdırmaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="bba3b-117">Printing Overview</span></span>](printing-overview.md)
