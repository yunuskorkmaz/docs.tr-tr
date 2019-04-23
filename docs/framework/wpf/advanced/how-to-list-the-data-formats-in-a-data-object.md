---
title: 'Nasıl yapılır: Bir Veri Nesnesi İçinde Veri Biçimlerini Listeleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- drag-and-drop [WPF], listing data formats
- DataFormats class [WPF]
- data formats [WPF], listing
ms.assetid: 18e7ba4b-ccef-4815-ae2d-3a32891010c0
ms.openlocfilehash: f8230eac33a18a0d99cc757d54c2b901c1afe977
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59077751"
---
# <a name="how-to-list-the-data-formats-in-a-data-object"></a><span data-ttu-id="53f99-102">Nasıl yapılır: Bir Veri Nesnesi İçinde Veri Biçimlerini Listeleme</span><span class="sxs-lookup"><span data-stu-id="53f99-102">How to: List the Data Formats in a Data Object</span></span>
<span data-ttu-id="53f99-103">Aşağıdaki örnekler nasıl kullanılacağını <xref:System.Windows.DataObject.GetFormats%2A> yöntemi aşırı bir veri nesnesi içinde kullanılabilir olan her veri biçimi belirten bir dize dizisi alın.</span><span class="sxs-lookup"><span data-stu-id="53f99-103">The following examples show how to use the <xref:System.Windows.DataObject.GetFormats%2A> method overloads get an array of strings denoting each data format that is available in a data object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="53f99-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="53f99-104">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="53f99-105">Açıklama</span><span class="sxs-lookup"><span data-stu-id="53f99-105">Description</span></span>  
 <span data-ttu-id="53f99-106">Aşağıdaki örnek kod <xref:System.Windows.DataObject.GetFormats%2A> (hem yerel hem de otomatik dönüştürülebilir) bir veri nesnesi içinde kullanılabilir olan tüm veri biçimlerini belirten bir dize dizisi almak için aşırı yükleme.</span><span class="sxs-lookup"><span data-stu-id="53f99-106">The following example code uses the <xref:System.Windows.DataObject.GetFormats%2A> overload to get an array of strings denoting all data formats available in a data object (both native and auto-convertible).</span></span>  
  
### <a name="code"></a><span data-ttu-id="53f99-107">Kod</span><span class="sxs-lookup"><span data-stu-id="53f99-107">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getalldataformats)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getalldataformats)]  
  
## <a name="example"></a><span data-ttu-id="53f99-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="53f99-108">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="53f99-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="53f99-109">Description</span></span>  
 <span data-ttu-id="53f99-110">Aşağıdaki örnek kod <xref:System.Windows.DataObject.GetFormats%2A> yalnızca bir veri nesnesi (otomatik dönüştürülebilir veri biçimleri filtrelenir) kullanılabilir veri biçimlerini belirten bir dize dizisi almak için aşırı yükleme.</span><span class="sxs-lookup"><span data-stu-id="53f99-110">The following example code uses the <xref:System.Windows.DataObject.GetFormats%2A> overload to get an array of strings denoting only data formats available in a data object (auto-convertible data formats are filtered).</span></span>  
  
### <a name="code"></a><span data-ttu-id="53f99-111">Kod</span><span class="sxs-lookup"><span data-stu-id="53f99-111">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats_NativeOnly](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getalldataformats_nativeonly)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats_NativeOnly](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getalldataformats_nativeonly)]  
  
## <a name="see-also"></a><span data-ttu-id="53f99-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="53f99-112">See also</span></span>

- <xref:System.Windows.IDataObject>
- [<span data-ttu-id="53f99-113">Sürükleme ve Bırakmaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="53f99-113">Drag and Drop Overview</span></span>](drag-and-drop-overview.md)
