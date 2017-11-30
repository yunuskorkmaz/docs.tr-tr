---
title: "Nasıl yapılır: Bir Veri Nesnesi İçinde Veri Biçimlerini Listeleme"
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
- drag-and-drop [WPF], listing data formats
- DataFormats class [WPF]
- data formats [WPF], listing
ms.assetid: 18e7ba4b-ccef-4815-ae2d-3a32891010c0
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9ef5657aefdf1c229b4f1749881cce1148435a8d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-list-the-data-formats-in-a-data-object"></a><span data-ttu-id="12ba1-102">Nasıl yapılır: Bir Veri Nesnesi İçinde Veri Biçimlerini Listeleme</span><span class="sxs-lookup"><span data-stu-id="12ba1-102">How to: List the Data Formats in a Data Object</span></span>
<span data-ttu-id="12ba1-103">Aşağıdaki örnekler nasıl kullanılacağını <xref:System.Windows.DataObject.GetFormats%2A> yöntemi aşırı alma bir veri nesnesi içinde kullanılabilir olan her veri biçimi belirten bir dizeler dizisi.</span><span class="sxs-lookup"><span data-stu-id="12ba1-103">The following examples show how to use the <xref:System.Windows.DataObject.GetFormats%2A> method overloads get an array of strings denoting each data format that is available in a data object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="12ba1-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="12ba1-104">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="12ba1-105">Açıklama</span><span class="sxs-lookup"><span data-stu-id="12ba1-105">Description</span></span>  
 <span data-ttu-id="12ba1-106">Aşağıdaki kod örneği kullanan <xref:System.Windows.DataObject.GetFormats%2A> bir veri nesnesi (hem yerel hem de otomatik dönüştürülebilir) içinde kullanılabilir tüm veri biçimlerini belirten bir dize dizisi almak için aşırı yükleme.</span><span class="sxs-lookup"><span data-stu-id="12ba1-106">The following example code uses the <xref:System.Windows.DataObject.GetFormats%2A> overload to get an array of strings denoting all data formats available in a data object (both native and auto-convertible).</span></span>  
  
### <a name="code"></a><span data-ttu-id="12ba1-107">Kod</span><span class="sxs-lookup"><span data-stu-id="12ba1-107">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getalldataformats)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getalldataformats)]  
  
## <a name="example"></a><span data-ttu-id="12ba1-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="12ba1-108">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="12ba1-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="12ba1-109">Description</span></span>  
 <span data-ttu-id="12ba1-110">Aşağıdaki kod örneği kullanan <xref:System.Windows.DataObject.GetFormats%2A> yalnızca bir veri nesnesi (otomatik dönüştürülebilir veri biçimleri filtrelenir) kullanılabilir veri biçimlerini belirten bir dize dizisi almak için aşırı yükleme.</span><span class="sxs-lookup"><span data-stu-id="12ba1-110">The following example code uses the <xref:System.Windows.DataObject.GetFormats%2A> overload to get an array of strings denoting only data formats available in a data object (auto-convertible data formats are filtered).</span></span>  
  
### <a name="code"></a><span data-ttu-id="12ba1-111">Kod</span><span class="sxs-lookup"><span data-stu-id="12ba1-111">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats_NativeOnly](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getalldataformats_nativeonly)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats_NativeOnly](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getalldataformats_nativeonly)]  
  
## <a name="see-also"></a><span data-ttu-id="12ba1-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="12ba1-112">See Also</span></span>  
 <xref:System.Windows.IDataObject>  
 [<span data-ttu-id="12ba1-113">Sürükle ve bırak genel bakış</span><span class="sxs-lookup"><span data-stu-id="12ba1-113">Drag and Drop Overview</span></span>](../../../../docs/framework/wpf/advanced/drag-and-drop-overview.md)
