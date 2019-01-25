---
title: 'Nasıl yapılır: Belirli Veri Biçiminde Veri Alma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- drag-and-drop [WPF], retrieving data
- DataFormats class [WPF], retrieving data
- DataObject class [WPF], retrieving data
ms.assetid: a625acf3-1144-44cd-add7-456aefc3859f
ms.openlocfilehash: d11374cbc70210e648e93a385c4a9fbca112c09f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54718305"
---
# <a name="how-to-retrieve-data-in-a-particular-data-format"></a><span data-ttu-id="731d3-102">Nasıl yapılır: Belirli Veri Biçiminde Veri Alma</span><span class="sxs-lookup"><span data-stu-id="731d3-102">How to: Retrieve Data in a Particular Data Format</span></span>
<span data-ttu-id="731d3-103">Aşağıdaki örnekler, belirli bir biçimdeki veri nesnesinde veri almak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="731d3-103">The following examples show how to retrieve data from a data object in a specified format.</span></span>  
  
## <a name="example"></a><span data-ttu-id="731d3-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="731d3-104">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="731d3-105">Açıklama</span><span class="sxs-lookup"><span data-stu-id="731d3-105">Description</span></span>  
 <span data-ttu-id="731d3-106">Aşağıdaki örnek kod <xref:System.Windows.DataObject.GetDataPresent%28System.String%29> (yerel olarak veya otomatik dönüştürme), belirtilen veri biçimlendirme ilk denetlenecek aşırı yüklemesi kullanılabilir; belirtilen biçim varsa, örnek verileri kullanarak alır <xref:System.Windows.DataObject.GetData%28System.String%29> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="731d3-106">The following example code uses the <xref:System.Windows.DataObject.GetDataPresent%28System.String%29> overload to first check if a specified data format is available (natively or by auto-convert); if the specified format is available, the example retrieves the data by using the <xref:System.Windows.DataObject.GetData%28System.String%29> method.</span></span>  
  
### <a name="code"></a><span data-ttu-id="731d3-107">Kod</span><span class="sxs-lookup"><span data-stu-id="731d3-107">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getspecificdataformat)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getspecificdataformat)]  
  
## <a name="example"></a><span data-ttu-id="731d3-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="731d3-108">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="731d3-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="731d3-109">Description</span></span>  
 <span data-ttu-id="731d3-110">Aşağıdaki örnek kod <xref:System.Windows.DataObject.GetDataPresent%28System.String%2CSystem.Boolean%29> ilk belirtilen veri biçimi yerel olarak kullanılabilir olup olmadığını denetlemek için aşırı yükleme (otomatik dönüştürülebilir veri biçimleri filtrelenir); belirtilen biçim varsa, örnek verileri kullanarakalır<xref:System.Windows.DataObject.GetData%28System.String%29>yöntemi.</span><span class="sxs-lookup"><span data-stu-id="731d3-110">The following example code uses the <xref:System.Windows.DataObject.GetDataPresent%28System.String%2CSystem.Boolean%29> overload to first check if a specified data format is available natively (auto-convertible data formats are filtered); if the specified format is available, the example retrieves the data by using the <xref:System.Windows.DataObject.GetData%28System.String%29> method.</span></span>  
  
### <a name="code"></a><span data-ttu-id="731d3-111">Kod</span><span class="sxs-lookup"><span data-stu-id="731d3-111">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat_Native](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getspecificdataformat_native)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat_Native](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getspecificdataformat_native)]  
  
## <a name="see-also"></a><span data-ttu-id="731d3-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="731d3-112">See also</span></span>
- <xref:System.Windows.IDataObject>
- [<span data-ttu-id="731d3-113">Sürükleme ve Bırakmaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="731d3-113">Drag and Drop Overview</span></span>](../../../../docs/framework/wpf/advanced/drag-and-drop-overview.md)
