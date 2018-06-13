---
title: 'Nasıl yapılır: Özel Nesneler Üzerinde Doğrulama Mantığı Uygulama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- checking for validation errors [WPF]
- validation errors [WPF], checking for
- implementing validation logic on custom objects [WPF]
- custom objects [WPF], implementing validation logic on
ms.assetid: 751fda9b-44f9-4d63-b4f2-1df07ac41e0f
ms.openlocfilehash: dbeddb5eb6996d5758717ddd2d4d5af0b6f57f3c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33555970"
---
# <a name="how-to-implement-validation-logic-on-custom-objects"></a>Nasıl yapılır: Özel Nesneler Üzerinde Doğrulama Mantığı Uygulama
Bu örnek, özel bir nesne üzerinde doğrulama mantığı uygulamak ve onu bağladıktan gösterilmektedir.  
  
## <a name="example"></a>Örnek  
 Kaynak nesne uyguluyorsa iş katmanında doğrulama mantığını sağlayabilirsiniz <xref:System.ComponentModel.IDataErrorInfo>, aşağıdaki örnekte olduğu gibi:  
  
 [!code-csharp[BusinessLayerValidation#IDataErrorInfo](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BusinessLayerValidation/CSharp/Data.cs#idataerrorinfo)]
 [!code-vb[BusinessLayerValidation#IDataErrorInfo](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BusinessLayerValidation/VisualBasic/Data.vb#idataerrorinfo)]  
  
 Aşağıdaki örnekte, metin kutusunun metin özelliği bağlar `Age` özelliği `Person` verilen kaynak bildirimine bağlamak için kullanılabilir hale nesne `x:Key``data`. <xref:System.Windows.Controls.DataErrorValidationRule> Tarafından gerçekleştirilen doğrulama hatalarını denetler <xref:System.ComponentModel.IDataErrorInfo> uygulaması.  
  
 [!code-xaml[BusinessLayerValidation#BoundTextBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BusinessLayerValidation/CSharp/Window1.xaml#boundtextbox)]  
  
 Alternatif olarak, kullanmak yerine <xref:System.Windows.Controls.DataErrorValidationRule>, ayarlayabileceğiniz <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A> özelliğine `true`.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Controls.ExceptionValidationRule>  
 [Bağlama Doğrulaması Uygulama](../../../../docs/framework/wpf/data/how-to-implement-binding-validation.md)  
 [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
