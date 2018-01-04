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
ms.workload: dotnet
ms.openlocfilehash: cb27928031b551da2957aab0696646e8adc3f803
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-list-the-data-formats-in-a-data-object"></a>Nasıl yapılır: Bir Veri Nesnesi İçinde Veri Biçimlerini Listeleme
Aşağıdaki örnekler nasıl kullanılacağını <xref:System.Windows.DataObject.GetFormats%2A> yöntemi aşırı alma bir veri nesnesi içinde kullanılabilir olan her veri biçimi belirten bir dizeler dizisi.  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Açıklama  
 Aşağıdaki kod örneği kullanan <xref:System.Windows.DataObject.GetFormats%2A> bir veri nesnesi (hem yerel hem de otomatik dönüştürülebilir) içinde kullanılabilir tüm veri biçimlerini belirten bir dize dizisi almak için aşırı yükleme.  
  
### <a name="code"></a>Kod  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getalldataformats)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getalldataformats)]  
  
## <a name="example"></a>Örnek  
  
### <a name="description"></a>Açıklama  
 Aşağıdaki kod örneği kullanan <xref:System.Windows.DataObject.GetFormats%2A> yalnızca bir veri nesnesi (otomatik dönüştürülebilir veri biçimleri filtrelenir) kullanılabilir veri biçimlerini belirten bir dize dizisi almak için aşırı yükleme.  
  
### <a name="code"></a>Kod  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats_NativeOnly](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getalldataformats_nativeonly)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats_NativeOnly](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getalldataformats_nativeonly)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.IDataObject>  
 [Sürükleme ve Bırakmaya Genel Bakış](../../../../docs/framework/wpf/advanced/drag-and-drop-overview.md)
