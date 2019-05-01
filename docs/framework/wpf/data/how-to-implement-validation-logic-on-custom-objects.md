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
ms.openlocfilehash: 8520504757e9e9ec9557b84ca2608b4cb99daf62
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61931418"
---
# <a name="how-to-implement-validation-logic-on-custom-objects"></a><span data-ttu-id="f059e-102">Nasıl yapılır: Özel Nesneler Üzerinde Doğrulama Mantığı Uygulama</span><span class="sxs-lookup"><span data-stu-id="f059e-102">How to: Implement Validation Logic on Custom Objects</span></span>
<span data-ttu-id="f059e-103">Bu örnekte, özel bir nesne üzerinde doğrulama mantığı uygulama ve ona bağlama gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f059e-103">This example shows how to implement validation logic on a custom object and then bind to it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f059e-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="f059e-104">Example</span></span>  
 <span data-ttu-id="f059e-105">Eğer kaynak nesneniz uyguluyorsa iş katmanı üzerinde doğrulama mantığı sağlayabilirsiniz <xref:System.ComponentModel.IDataErrorInfo>, tanımlayan aşağıdaki örnekte olduğu gibi bir `Person` uygulayan nesne <xref:System.ComponentModel.IDataErrorInfo>:</span><span class="sxs-lookup"><span data-stu-id="f059e-105">You can provide validation logic on the business layer if your source object implements <xref:System.ComponentModel.IDataErrorInfo>, as in the following example, which defines a `Person` object that implements <xref:System.ComponentModel.IDataErrorInfo>:</span></span>  
  
 [!code-csharp[BusinessLayerValidation#IDataErrorInfo](~/samples/snippets/csharp/VS_Snippets_Wpf/BusinessLayerValidation/CSharp/Data.cs#idataerrorinfo)]
 [!code-vb[BusinessLayerValidation#IDataErrorInfo](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BusinessLayerValidation/VisualBasic/Data.vb#idataerrorinfo)]  
  
 <span data-ttu-id="f059e-106">Aşağıdaki örnekte, metin kutusunun metin özelliği bağlar `Person.Age` verilen kaynak bildirimine bağlamak için kullanılabilir hale getirdiği özelliği `x:Key` `data`.</span><span class="sxs-lookup"><span data-stu-id="f059e-106">In the following example, the text property of the text box binds to the `Person.Age` property, which has been made available for binding through a resource declaration that is given the `x:Key` `data`.</span></span> <span data-ttu-id="f059e-107"><xref:System.Windows.Controls.DataErrorValidationRule> Tarafından gerçekleştirilen doğrulama hatalarını denetler <xref:System.ComponentModel.IDataErrorInfo> uygulaması.</span><span class="sxs-lookup"><span data-stu-id="f059e-107">The <xref:System.Windows.Controls.DataErrorValidationRule> checks for the validation errors raised by the <xref:System.ComponentModel.IDataErrorInfo> implementation.</span></span>  
  
 [!code-xaml[BusinessLayerValidation#BoundTextBox](~/samples/snippets/csharp/VS_Snippets_Wpf/BusinessLayerValidation/CSharp/Window1.xaml?highlight=8,11-19,25-42)]  
  
 <span data-ttu-id="f059e-108">Alternatif olarak, kullanmak yerine <xref:System.Windows.Controls.DataErrorValidationRule>, ayarlayabileceğiniz <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A> özelliğini `true`.</span><span class="sxs-lookup"><span data-stu-id="f059e-108">Alternatively, instead of using the <xref:System.Windows.Controls.DataErrorValidationRule>, you can set the <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A> property to `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f059e-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f059e-109">See also</span></span>

- <xref:System.Windows.Controls.ExceptionValidationRule>
- [<span data-ttu-id="f059e-110">Bağlama Doğrulaması Uygulama</span><span class="sxs-lookup"><span data-stu-id="f059e-110">Implement Binding Validation</span></span>](how-to-implement-binding-validation.md)
- [<span data-ttu-id="f059e-111">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="f059e-111">How-to Topics</span></span>](data-binding-how-to-topics.md)
