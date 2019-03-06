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
ms.openlocfilehash: c8e9f24a0e991fa44ddd3f4d778cc7ba640ae9c3
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57370182"
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
