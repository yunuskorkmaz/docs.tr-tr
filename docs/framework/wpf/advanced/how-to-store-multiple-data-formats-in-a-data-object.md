---
title: 'Nasıl yapılır: Veri Nesnesinde Birden Çok Veri Biçimini Depolama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataObject class [WPF], storing multiple formats
- DataFormats class [WPF], storing multiple formats
- drag-and-drop [WPF], storing multiple formats
ms.assetid: 941ace29-29c4-4c26-b75b-ea7d06aa0d69
ms.openlocfilehash: 9e261f3f00c28a0a15343e2691048ad022f1be7c
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57351079"
---
# <a name="how-to-store-multiple-data-formats-in-a-data-object"></a><span data-ttu-id="e1a5d-102">Nasıl yapılır: Veri Nesnesinde Birden Çok Veri Biçimini Depolama</span><span class="sxs-lookup"><span data-stu-id="e1a5d-102">How to: Store Multiple Data Formats in a Data Object</span></span>
<span data-ttu-id="e1a5d-103">Aşağıdaki örnek nasıl kullanılacağını gösterir <xref:System.Windows.DataObject.SetData%28System.String%2CSystem.Object%29> birden çok biçimde veri nesnesinde veri eklemek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e1a5d-103">The following example shows how to use the <xref:System.Windows.DataObject.SetData%28System.String%2CSystem.Object%29> method to add data to a data object in multiple formats.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e1a5d-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="e1a5d-104">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="e1a5d-105">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e1a5d-105">Description</span></span>  
  
### <a name="code"></a><span data-ttu-id="e1a5d-106">Kod</span><span class="sxs-lookup"><span data-stu-id="e1a5d-106">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_StoreMultipleFormats](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_storemultipleformats)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_StoreMultipleFormats](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_storemultipleformats)]  
  
## <a name="see-also"></a><span data-ttu-id="e1a5d-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e1a5d-107">See also</span></span>
- <xref:System.Windows.IDataObject>
- [<span data-ttu-id="e1a5d-108">Sürükleme ve Bırakmaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="e1a5d-108">Drag and Drop Overview</span></span>](drag-and-drop-overview.md)
