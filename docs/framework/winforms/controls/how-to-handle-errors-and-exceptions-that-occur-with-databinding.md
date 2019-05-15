---
title: 'Nasıl yapılır: Veri Bağlamada Oluşan Hataları ve Özel Durumları İşleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- error handling [Windows Forms], examples
- data binding [Windows Forms], examples
- examples [Windows Forms], error handling
- error handling [Windows Forms], data binding
- data binding [Windows Forms], error handling
- BindingSource component [Windows Forms], handling errors and exceptions
ms.assetid: eddc5bad-9513-47df-ab28-f02d8dff7892
ms.openlocfilehash: 14326d793be3ee71022a7a1e7398b9af469aab10
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65592452"
---
# <a name="how-to-handle-errors-and-exceptions-that-occur-with-databinding"></a><span data-ttu-id="0217d-102">Nasıl yapılır: Veri Bağlamada Oluşan Hataları ve Özel Durumları İşleme</span><span class="sxs-lookup"><span data-stu-id="0217d-102">How to: Handle Errors and Exceptions that Occur with Databinding</span></span>
<span data-ttu-id="0217d-103">Denetimlere bağlayabilirsiniz önerilmesine özel durumlar ve hatalar temel alınan iş nesnelerde ortaya çıkar.</span><span class="sxs-lookup"><span data-stu-id="0217d-103">Oftentimes exceptions and errors occur on the underlying business objects when you bind them to controls.</span></span> <span data-ttu-id="0217d-104">Bu hatalar ve özel durumlar ıntercept ve sonra kurtarmak veya hata bilgilerini kullanıcıya işleyerek geçirmek <xref:System.Windows.Forms.Binding.BindingComplete> belirli bir olay <xref:System.Windows.Forms.Binding>, <xref:System.Windows.Forms.BindingSource>, veya <xref:System.Windows.Forms.CurrencyManager> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="0217d-104">You can intercept these errors and exceptions and then either recover or pass the error information to the user by handling the <xref:System.Windows.Forms.Binding.BindingComplete> event for a particular <xref:System.Windows.Forms.Binding>, <xref:System.Windows.Forms.BindingSource>, or <xref:System.Windows.Forms.CurrencyManager> component.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0217d-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="0217d-105">Example</span></span>  
 <span data-ttu-id="0217d-106">Bu kod örneği, hataları ve veri bağlama işlemi sırasında oluşan özel durumlarının nasıl ele alınacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="0217d-106">This code example demonstrates how to handle errors and exceptions that occur during a data-binding operation.</span></span> <span data-ttu-id="0217d-107">Hataları işleyerek ıntercept yapmayı gösteren <xref:System.Windows.Forms.Binding.BindingComplete?displayProperty=nameWithType> olayı <xref:System.Windows.Forms.Binding> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="0217d-107">It demonstrates how to intercept errors by handling the <xref:System.Windows.Forms.Binding.BindingComplete?displayProperty=nameWithType> event of the <xref:System.Windows.Forms.Binding> objects.</span></span> <span data-ttu-id="0217d-108">Hataları ve özel durumları bu olayı işleme tarafından müdahale için bağını biçimlendirme etkinleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="0217d-108">In order to intercept errors and exceptions by handling this event, you must enable formatting for the binding.</span></span> <span data-ttu-id="0217d-109">Bağlama oluşturulmuş ya da eklenen bağlama koleksiyonuna veya ayarlayarak biçimlendirme etkinleştirebilirsiniz <xref:System.Windows.Forms.Binding.FormattingEnabled%2A> özelliğini `true`.</span><span class="sxs-lookup"><span data-stu-id="0217d-109">You can enable formatting when the binding is constructed or added to the binding collection, or by setting the <xref:System.Windows.Forms.Binding.FormattingEnabled%2A> property to `true`.</span></span>  
  
 [!code-cpp[System.Windows.Forms.DataConnectorBindingComplete#3](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorBindingComplete/CPP/form1.cpp#3)]
 [!code-csharp[System.Windows.Forms.DataConnectorBindingComplete#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorBindingComplete/CS/form1.cs#3)]
 [!code-vb[System.Windows.Forms.DataConnectorBindingComplete#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorBindingComplete/VB/form1.vb#3)]  
  
 <span data-ttu-id="0217d-110">Ne zaman kodu çalıştıran ve boş bir dize bölümü ad veya değer 100'den daha az girilen parça numarası için bir ileti kutusu görünür girilir.</span><span class="sxs-lookup"><span data-stu-id="0217d-110">When the code is running and an empty string is entered for the part name or a value less than 100 is entered for the part number, a message box appears.</span></span> <span data-ttu-id="0217d-111">Bu bir işleme sonucudur <xref:System.Windows.Forms.Binding.BindingComplete?displayProperty=nameWithType> bu metin bağlamaları için olay.</span><span class="sxs-lookup"><span data-stu-id="0217d-111">This is a result of handling the <xref:System.Windows.Forms.Binding.BindingComplete?displayProperty=nameWithType> event for these textbox bindings.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="0217d-112">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="0217d-112">Compiling the Code</span></span>  
 <span data-ttu-id="0217d-113">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="0217d-113">This example requires:</span></span>  
  
- <span data-ttu-id="0217d-114">Sistem, System.Drawing ve System.Windows.Forms öğelerini derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="0217d-114">References to the System, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0217d-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0217d-115">See also</span></span>

- <xref:System.Windows.Forms.Binding.BindingComplete?displayProperty=nameWithType>
- <xref:System.Windows.Forms.BindingSource.BindingComplete?displayProperty=nameWithType>
- [<span data-ttu-id="0217d-116">BindingSource Bileşeni</span><span class="sxs-lookup"><span data-stu-id="0217d-116">BindingSource Component</span></span>](bindingsource-component.md)
