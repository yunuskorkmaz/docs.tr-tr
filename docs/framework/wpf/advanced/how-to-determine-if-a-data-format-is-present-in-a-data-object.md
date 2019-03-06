---
title: 'Nasıl yapılır: Veri Nesnesinde Veri Biçiminin Olup Olmadığını Belirleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataFormats class [WPF]
- drag-and-drop [WPF], data formats present
- data formats [WPF], determining if present
ms.assetid: e487a454-c9fc-4e53-aeaa-c458d059ad4c
ms.openlocfilehash: 57190b94988c8ee557e99836a8e8500bfb622f2e
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57379178"
---
# <a name="how-to-determine-if-a-data-format-is-present-in-a-data-object"></a>Nasıl yapılır: Veri Nesnesinde Veri Biçiminin Olup Olmadığını Belirleme
Aşağıdaki örnekler çeşitli kullanmayı <xref:System.Windows.DataObject.GetDataPresent%2A> yöntemi belirli veri biçiminde veri nesnesinde var olup olmadığını sorgulamak için aşırı yüklemeleri.  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Açıklama  
 Aşağıdaki örnek kod <xref:System.Windows.DataObject.GetDataPresent%28System.String%29> aşırı yükleme tanımlayıcısı dizesindeki bir belirli veri biçiminde varlığını sorgulanamıyor.  
  
### <a name="code"></a>Kod  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_QueryDataFormats_String](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_querydataformats_string)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_QueryDataFormats_String](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_querydataformats_string)]  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Açıklama  
 Aşağıdaki örnek kod <xref:System.Windows.DataObject.GetDataPresent%28System.Type%29> sorgu varlığını türüne göre belirli veri biçimi için aşırı yükleme.  
  
### <a name="code"></a>Kod  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_QueryDataFormats_Type](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_querydataformats_type)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_QueryDataFormats_Type](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_querydataformats_type)]  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Açıklama  
 Aşağıdaki örnek kod <xref:System.Windows.DataObject.GetDataPresent%28System.String%2CSystem.Boolean%29> tanımlayıcı dizesi tarafından aşırı sorgulamak için veri ve nasıl işlemesi gerektiğini otomatik dönüştürülebilir veri biçimleri belirleme.  
  
### <a name="code"></a>Kod  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_QueryDataFormats_Autoconvert](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_querydataformats_autoconvert)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_QueryDataFormats_Autoconvert](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_querydataformats_autoconvert)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.IDataObject>
