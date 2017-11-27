---
title: "Nasıl yapılır: Belirli Veri Biçiminde Veri Alma"
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
helpviewer_keywords:
- drag-and-drop [WPF], retrieving data
- DataFormats class [WPF], retrieving data
- DataObject class [WPF], retrieving data
ms.assetid: a625acf3-1144-44cd-add7-456aefc3859f
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8e6513fd6d8d443b76059626c0e40991e35830c6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-retrieve-data-in-a-particular-data-format"></a><span data-ttu-id="85505-102">Nasıl yapılır: Belirli Veri Biçiminde Veri Alma</span><span class="sxs-lookup"><span data-stu-id="85505-102">How to: Retrieve Data in a Particular Data Format</span></span>
<span data-ttu-id="85505-103">Aşağıdaki örnekler belirtilen biçimde veri nesnesinden verileri almak üzere nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="85505-103">The following examples show how to retrieve data from a data object in a specified format.</span></span>  
  
## <a name="example"></a><span data-ttu-id="85505-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="85505-104">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="85505-105">Açıklama</span><span class="sxs-lookup"><span data-stu-id="85505-105">Description</span></span>  
 <span data-ttu-id="85505-106">Aşağıdaki kod örneği kullanan <xref:System.Windows.DataObject.GetDataPresent%28System.String%29> (yerel olarak veya otomatik dönüştürerek) belirtilen bir veri biçimi, ilk denetlenecek aşırı kullanılabilir; belirtilen biçim kullanılabilir durumdaysa, örnek verileri kullanarak alır <xref:System.Windows.DataObject.GetData%28System.String%29> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="85505-106">The following example code uses the <xref:System.Windows.DataObject.GetDataPresent%28System.String%29> overload to first check if a specified data format is available (natively or by auto-convert); if the specified format is available, the example retrieves the data by using the <xref:System.Windows.DataObject.GetData%28System.String%29> method.</span></span>  
  
### <a name="code"></a><span data-ttu-id="85505-107">Kod</span><span class="sxs-lookup"><span data-stu-id="85505-107">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getspecificdataformat)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getspecificdataformat)]  
  
## <a name="example"></a><span data-ttu-id="85505-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="85505-108">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="85505-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="85505-109">Description</span></span>  
 <span data-ttu-id="85505-110">Aşağıdaki kod örneği kullanan <xref:System.Windows.DataObject.GetDataPresent%28System.String%2CSystem.Boolean%29> ilk belirtilen veri biçiminin yerel olarak kullanılabilir olup olmadığını denetlemek için aşırı yükleme (otomatik dönüştürülebilir veri biçimleri filtrelenir); belirtilen biçim kullanılabilir durumdaysa, örnek verileri kullanarakalır<xref:System.Windows.DataObject.GetData%28System.String%29>yöntemi.</span><span class="sxs-lookup"><span data-stu-id="85505-110">The following example code uses the <xref:System.Windows.DataObject.GetDataPresent%28System.String%2CSystem.Boolean%29> overload to first check if a specified data format is available natively (auto-convertible data formats are filtered); if the specified format is available, the example retrieves the data by using the <xref:System.Windows.DataObject.GetData%28System.String%29> method.</span></span>  
  
### <a name="code"></a><span data-ttu-id="85505-111">Kod</span><span class="sxs-lookup"><span data-stu-id="85505-111">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat_Native](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getspecificdataformat_native)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat_Native](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getspecificdataformat_native)]  
  
## <a name="see-also"></a><span data-ttu-id="85505-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="85505-112">See Also</span></span>  
 <xref:System.Windows.IDataObject>  
 [<span data-ttu-id="85505-113">Sürükle ve bırak genel bakış</span><span class="sxs-lookup"><span data-stu-id="85505-113">Drag and Drop Overview</span></span>](../../../../docs/framework/wpf/advanced/drag-and-drop-overview.md)
