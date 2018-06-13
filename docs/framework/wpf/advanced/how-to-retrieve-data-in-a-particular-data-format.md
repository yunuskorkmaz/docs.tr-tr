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
# <a name="how-to-retrieve-data-in-a-particular-data-format"></a>Nasıl yapılır: Belirli Veri Biçiminde Veri Alma
Aşağıdaki örnekler belirtilen biçimde veri nesnesinden verileri almak üzere nasıl gösterir.  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Açıklama  
 Aşağıdaki kod örneği kullanan <xref:System.Windows.DataObject.GetDataPresent%28System.String%29> (yerel olarak veya otomatik dönüştürerek) belirtilen bir veri biçimi, ilk denetlenecek aşırı kullanılabilir; belirtilen biçim kullanılabilir durumdaysa, örnek verileri kullanarak alır <xref:System.Windows.DataObject.GetData%28System.String%29> yöntemi.  
  
### <a name="code"></a>Kod  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getspecificdataformat)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getspecificdataformat)]  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Açıklama  
 Aşağıdaki kod örneği kullanan <xref:System.Windows.DataObject.GetDataPresent%28System.String%2CSystem.Boolean%29> ilk belirtilen veri biçiminin yerel olarak kullanılabilir olup olmadığını denetlemek için aşırı yükleme (otomatik dönüştürülebilir veri biçimleri filtrelenir); belirtilen biçim kullanılabilir durumdaysa, örnek verileri kullanarakalır<xref:System.Windows.DataObject.GetData%28System.String%29>yöntemi.  
  
### <a name="code"></a>Kod  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat_Native](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getspecificdataformat_native)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetSpecificDataFormat_Native](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getspecificdataformat_native)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.IDataObject>  
 [Sürükleme ve Bırakmaya Genel Bakış](../../../../docs/framework/wpf/advanced/drag-and-drop-overview.md)
