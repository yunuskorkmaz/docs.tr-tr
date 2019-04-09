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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59077751"
---
# <a name="how-to-list-the-data-formats-in-a-data-object"></a>Nasıl yapılır: Bir Veri Nesnesi İçinde Veri Biçimlerini Listeleme
Aşağıdaki örnekler nasıl kullanılacağını <xref:System.Windows.DataObject.GetFormats%2A> yöntemi aşırı bir veri nesnesi içinde kullanılabilir olan her veri biçimi belirten bir dize dizisi alın.  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Açıklama  
 Aşağıdaki örnek kod <xref:System.Windows.DataObject.GetFormats%2A> (hem yerel hem de otomatik dönüştürülebilir) bir veri nesnesi içinde kullanılabilir olan tüm veri biçimlerini belirten bir dize dizisi almak için aşırı yükleme.  
  
### <a name="code"></a>Kod  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getalldataformats)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getalldataformats)]  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Açıklama  
 Aşağıdaki örnek kod <xref:System.Windows.DataObject.GetFormats%2A> yalnızca bir veri nesnesi (otomatik dönüştürülebilir veri biçimleri filtrelenir) kullanılabilir veri biçimlerini belirten bir dize dizisi almak için aşırı yükleme.  
  
### <a name="code"></a>Kod  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats_NativeOnly](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getalldataformats_nativeonly)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats_NativeOnly](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getalldataformats_nativeonly)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.IDataObject>
- [Sürükleme ve Bırakmaya Genel Bakış](drag-and-drop-overview.md)
