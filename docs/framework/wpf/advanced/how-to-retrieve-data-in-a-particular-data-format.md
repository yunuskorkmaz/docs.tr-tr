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
ms.openlocfilehash: 405fff1b586207249fbabafb28791ffa2901cf49
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33545113"
---
# <a name="how-to-retrieve-data-in-a-particular-data-format"></a><span data-ttu-id="a3268-102">Nasıl yapılır: Belirli Veri Biçiminde Veri Alma</span><span class="sxs-lookup"><span data-stu-id="a3268-102">How to: Retrieve Data in a Particular Data Format</span></span>
<span data-ttu-id="a3268-103">Aşağıdaki örnekler belirtilen biçimde veri nesnesinden verileri almak üzere nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="a3268-103">The following examples show how to retrieve data from a data object in a specified format.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a3268-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="a3268-104">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="a3268-105">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a3268-105">Description</span></span>  
 <span data-ttu-id="a3268-106">Aşağıdaki kod örneği kullanan <xref:System.Windows.DataObject.GetDataPresent%28System.String%29> (yerel olarak veya otomatik dönüştürerek) belirtilen bir veri biçimi, ilk denetlenecek aşırı kullanılabilir; belirtilen biçim kullanılabilir durumdaysa, örnek verileri kullanarak alır <xref:System.Windows.DataObject.GetData%28System.String%29> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="a3268-106">The following example code uses the <xref:System.Windows.DataObject.GetDataPresent%28System.String%29> overload to first check if a specified data format is available (natively or by auto-convert); if the specified format is available, the example retrieves the data by using the <xref:System.Windows.DataObject.GetData%28System.String%29> method.</span></span>  
  
### <a name="code"></a><span data-ttu-id="a3268-107">Kod</span><span class="sxs-lookup"><span data-stu-id="a3268-107">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getspecificdataformat)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getspecificdataformat)]  
  
## <a name="example"></a><span data-ttu-id="a3268-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="a3268-108">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="a3268-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a3268-109">Description</span></span>  
 <span data-ttu-id="a3268-110">Aşağıdaki kod örneği kullanan <xref:System.Windows.DataObject.GetDataPresent%28System.String%2CSystem.Boolean%29> ilk belirtilen veri biçiminin yerel olarak kullanılabilir olup olmadığını denetlemek için aşırı yükleme (otomatik dönüştürülebilir veri biçimleri filtrelenir); belirtilen biçim kullanılabilir durumdaysa, örnek verileri kullanarakalır<xref:System.Windows.DataObject.GetData%28System.String%29>yöntemi.</span><span class="sxs-lookup"><span data-stu-id="a3268-110">The following example code uses the <xref:System.Windows.DataObject.GetDataPresent%28System.String%2CSystem.Boolean%29> overload to first check if a specified data format is available natively (auto-convertible data formats are filtered); if the specified format is available, the example retrieves the data by using the <xref:System.Windows.DataObject.GetData%28System.String%29> method.</span></span>  
  
### <a name="code"></a><span data-ttu-id="a3268-111">Kod</span><span class="sxs-lookup"><span data-stu-id="a3268-111">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat_Native](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getspecificdataformat_native)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat_Native](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getspecificdataformat_native)]  
  
## <a name="see-also"></a><span data-ttu-id="a3268-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a3268-112">See Also</span></span>  
 <xref:System.Windows.IDataObject>  
 [<span data-ttu-id="a3268-113">Sürükleme ve Bırakmaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="a3268-113">Drag and Drop Overview</span></span>](../../../../docs/framework/wpf/advanced/drag-and-drop-overview.md)
