---
title: "Nasıl yapılır: Yazdırma Sistemi Nesnesi Özelliklerini Yansıma Olmadan Alma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: PrintSystemObject [WPF], getting properties
ms.assetid: 43560f28-183d-41c1-b9d1-de7c2552273e
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7d93919f691b51d5f177b074e5d9cef2c140458e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-get-print-system-object-properties-without-reflection"></a><span data-ttu-id="4afc8-102">Nasıl yapılır: Yazdırma Sistemi Nesnesi Özelliklerini Yansıma Olmadan Alma</span><span class="sxs-lookup"><span data-stu-id="4afc8-102">How to: Get Print System Object Properties Without Reflection</span></span>
<span data-ttu-id="4afc8-103">Nesne Özellikleri (ve bu özelliklerin türleri) belirtmek için yansıma kullanarak uygulama performansı düşürebilir.</span><span class="sxs-lookup"><span data-stu-id="4afc8-103">Using reflection to itemize the properties (and the types of those properties) on an object can slow application performance.</span></span> <span data-ttu-id="4afc8-104"><xref:System.Printing.IndexedProperties> Ad alanı, yansıma kullanarak bu bilgileri almak için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="4afc8-104">The <xref:System.Printing.IndexedProperties> namespace provides a means to getting this information with using reflection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4afc8-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="4afc8-105">Example</span></span>  
 <span data-ttu-id="4afc8-106">Bunu yapmak için adımlar aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="4afc8-106">The steps for doing this are as follows.</span></span>  
  
1.  <span data-ttu-id="4afc8-107">Türünün bir örneğini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="4afc8-107">Create an instance of the type.</span></span> <span data-ttu-id="4afc8-108">Aşağıdaki örnekte türüdür <xref:System.Printing.PrintQueue> birlikte türü [!INCLUDE[TLA#tla_winfx](../../../../includes/tlasharptla-winfx-md.md)], ancak iş öğesinden türetilen türler için neredeyse aynı kodu <xref:System.Printing.PrintSystemObject>.</span><span class="sxs-lookup"><span data-stu-id="4afc8-108">In the example below, the type is the <xref:System.Printing.PrintQueue> type that ships with [!INCLUDE[TLA#tla_winfx](../../../../includes/tlasharptla-winfx-md.md)], but nearly identical code should work for types that you derive from <xref:System.Printing.PrintSystemObject>.</span></span>  
  
2.  <span data-ttu-id="4afc8-109">Oluşturma bir <xref:System.Printing.IndexedProperties.PrintPropertyDictionary> türünden 's <xref:System.Printing.PrintSystemObject.PropertiesCollection%2A>.</span><span class="sxs-lookup"><span data-stu-id="4afc8-109">Create a <xref:System.Printing.IndexedProperties.PrintPropertyDictionary> from the type's <xref:System.Printing.PrintSystemObject.PropertiesCollection%2A>.</span></span> <span data-ttu-id="4afc8-110"><xref:System.Collections.DictionaryEntry.Value%2A> Bu sözlükteki her girdinin özelliği türetilen türlerden birinde bir nesnedir <xref:System.Printing.IndexedProperties.PrintProperty>.</span><span class="sxs-lookup"><span data-stu-id="4afc8-110">The <xref:System.Collections.DictionaryEntry.Value%2A> property of each entry in this dictionary is an object of one of the types derived from <xref:System.Printing.IndexedProperties.PrintProperty>.</span></span>  
  
3.  <span data-ttu-id="4afc8-111">Sözlük üyelerini sıralar.</span><span class="sxs-lookup"><span data-stu-id="4afc8-111">Enumerate the members of the dictionary.</span></span> <span data-ttu-id="4afc8-112">Bunların her biri için aşağıdakileri yapın.</span><span class="sxs-lookup"><span data-stu-id="4afc8-112">For each of them, do the following.</span></span>  
  
4.  <span data-ttu-id="4afc8-113">Her girdinin değerini yukarı doğru atayın <xref:System.Printing.IndexedProperties.PrintProperty> ve oluşturmak için kullanın bir <xref:System.Printing.IndexedProperties.PrintProperty> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="4afc8-113">Up-cast the value of each entry to <xref:System.Printing.IndexedProperties.PrintProperty> and use it to create a <xref:System.Printing.IndexedProperties.PrintProperty> object.</span></span>  
  
5.  <span data-ttu-id="4afc8-114">Türünü alın <xref:System.Printing.IndexedProperties.PrintProperty.Value%2A> her birinin <xref:System.Printing.IndexedProperties.PrintProperty> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="4afc8-114">Get the type of the <xref:System.Printing.IndexedProperties.PrintProperty.Value%2A> of each of the <xref:System.Printing.IndexedProperties.PrintProperty> object.</span></span>  
  
 [!code-csharp[GetPrintObjectPropertyTypesWithoutReflection#ShowPropertyTypesWithoutReflection](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GetPrintObjectPropertyTypesWithoutReflection/CSharp/Program.cs#showpropertytypeswithoutreflection)]
 [!code-vb[GetPrintObjectPropertyTypesWithoutReflection#ShowPropertyTypesWithoutReflection](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GetPrintObjectPropertyTypesWithoutReflection/visualbasic/program.vb#showpropertytypeswithoutreflection)]  
  
## <a name="see-also"></a><span data-ttu-id="4afc8-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4afc8-115">See Also</span></span>  
 <xref:System.Printing.IndexedProperties.PrintProperty>  
 <xref:System.Printing.PrintSystemObject>  
 <xref:System.Printing.IndexedProperties>  
 <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>  
 <xref:System.Printing.LocalPrintServer>  
 <xref:System.Printing.PrintQueue>  
 <xref:System.Collections.DictionaryEntry>  
 [<span data-ttu-id="4afc8-116">WPF'deki Belgeler</span><span class="sxs-lookup"><span data-stu-id="4afc8-116">Documents in WPF</span></span>](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [<span data-ttu-id="4afc8-117">Yazdırmaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="4afc8-117">Printing Overview</span></span>](../../../../docs/framework/wpf/advanced/printing-overview.md)
