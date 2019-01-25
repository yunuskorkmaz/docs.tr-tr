---
title: 'Nasıl yapılır: Özel Nesneler Üzerinde Doğrulama Mantığı Uygulama'
ms.date: 08/02/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- checking for validation errors [WPF]
- validation errors [WPF], checking for
- implementing validation logic on custom objects [WPF]
- custom objects [WPF], implementing validation logic on
ms.assetid: 751fda9b-44f9-4d63-b4f2-1df07ac41e0f
ms.openlocfilehash: e2b77ef65c92ae596c5620c9122dcf3db0bf9462
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54525995"
---
# <a name="how-to-implement-validation-logic-on-custom-objects"></a>Nasıl yapılır: Özel Nesneler Üzerinde Doğrulama Mantığı Uygulama
Bu örnekte, özel bir nesne üzerinde doğrulama mantığı uygulama ve ona bağlama gösterilmektedir.  
  
## <a name="example"></a>Örnek  
 Eğer kaynak nesneniz uyguluyorsa iş katmanı üzerinde doğrulama mantığı sağlayabilirsiniz <xref:System.ComponentModel.IDataErrorInfo>, tanımlayan aşağıdaki örnekte olduğu gibi bir `Person` uygulayan nesne <xref:System.ComponentModel.IDataErrorInfo>:  
  
 [!code-csharp[BusinessLayerValidation#IDataErrorInfo](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BusinessLayerValidation/CSharp/Data.cs#idataerrorinfo)]
 [!code-vb[BusinessLayerValidation#IDataErrorInfo](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BusinessLayerValidation/VisualBasic/Data.vb#idataerrorinfo)]  
  
 Aşağıdaki örnekte, metin kutusunun metin özelliği bağlar `Person.Age` verilen kaynak bildirimine bağlamak için kullanılabilir hale getirdiği özelliği `x:Key` `data`. <xref:System.Windows.Controls.DataErrorValidationRule> Tarafından gerçekleştirilen doğrulama hatalarını denetler <xref:System.ComponentModel.IDataErrorInfo> uygulaması.  
  
 [!code-xaml[BusinessLayerValidation#BoundTextBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BusinessLayerValidation/CSharp/Window1.xaml?highlight=8,11-19,25-42)]  
  
 Alternatif olarak, kullanmak yerine <xref:System.Windows.Controls.DataErrorValidationRule>, ayarlayabileceğiniz <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A> özelliğini `true`.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Controls.ExceptionValidationRule>
- [Bağlama Doğrulaması Uygulama](../../../../docs/framework/wpf/data/how-to-implement-binding-validation.md)
- [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
