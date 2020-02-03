---
title: Denetimleri DBNull veritabanı değerlerine bağlama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- BindingSource component [Windows Forms], binding to DBNull values
- examples [Windows Forms], BindingSource component
- controls [Windows Forms], binding to DBNull values
ms.assetid: 96494e6f-5f40-4f83-af97-bbd7192c2af8
ms.openlocfilehash: 175d7f5aee2540916480e2c55a485af1f9d16653
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746670"
---
# <a name="how-to-bind-windows-forms-controls-to-dbnull-database-values"></a><span data-ttu-id="1824c-102">Nasıl yapılır: Windows Forms Denetimlerini DBNull Veritabanı Değerlerine Bağlama</span><span class="sxs-lookup"><span data-stu-id="1824c-102">How to: Bind Windows Forms Controls to DBNull Database Values</span></span>
<span data-ttu-id="1824c-103">Windows Forms denetimleri bir veri kaynağına bağladığınızda ve veri kaynağı bir <xref:System.DBNull> değeri döndürürse, olayları işleme, biçimlendirme veya ayrıştırma olaylarını kullanmadan uygun bir değeri değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1824c-103">When you bind Windows Forms controls to a data source and the data source returns a <xref:System.DBNull> value, you can substitute an appropriate value without handling, formatting, or parsing events.</span></span> <span data-ttu-id="1824c-104"><xref:System.Windows.Forms.Binding.NullValue%2A> özelliği, veri kaynağı değerlerini biçimlendirirken veya ayrıştırırken belirtilen bir nesneye <xref:System.DBNull> dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="1824c-104">The <xref:System.Windows.Forms.Binding.NullValue%2A> property will convert <xref:System.DBNull> to a specified object when formatting or parsing the data source values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1824c-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="1824c-105">Example</span></span>  
 <span data-ttu-id="1824c-106">Aşağıdaki örnek, iki farklı durumda <xref:System.DBNull> bir değerin nasıl bağlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="1824c-106">The following example demonstrates how to bind a <xref:System.DBNull> value in two different situations.</span></span> <span data-ttu-id="1824c-107">İlki, bir dize özelliği için <xref:System.Windows.Forms.Binding.NullValue%2A> ayarlamayı gösterir; İkincisi, bir görüntü özelliği için <xref:System.Windows.Forms.Binding.NullValue%2A> ayarlamayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="1824c-107">The first demonstrates how to set the <xref:System.Windows.Forms.Binding.NullValue%2A> for a string property; the second demonstrates how to set the <xref:System.Windows.Forms.Binding.NullValue%2A> for an image property.</span></span>  
  
 [!code-csharp[System.Windows.Forms.BindingDBNull#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingDBNull/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingDBNull#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingDBNull/VB/form1.vb#1)]  
  
 <span data-ttu-id="1824c-108">Bağlantılı özelliğin türleri ve <xref:System.Windows.Forms.Binding.NullValue%2A> özelliği aynı olmalıdır veya hata oluşur, başka bir <xref:System.Windows.Forms.Binding.NullValue%2A> değeri işlenmeyecek.</span><span class="sxs-lookup"><span data-stu-id="1824c-108">The types of the bound property and the <xref:System.Windows.Forms.Binding.NullValue%2A> property must be the same or an error will result, and no further <xref:System.Windows.Forms.Binding.NullValue%2A> values will be processed.</span></span> <span data-ttu-id="1824c-109">Bu durumda, bir özel durum oluşturulmaz.</span><span class="sxs-lookup"><span data-stu-id="1824c-109">In this situation, an exception will not be thrown.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1824c-110">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="1824c-110">Compiling the Code</span></span>  
 <span data-ttu-id="1824c-111">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="1824c-111">This example requires:</span></span>  
  
- <span data-ttu-id="1824c-112">System, System. Data, System. Drawing ve System. Windows. Forms derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="1824c-112">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1824c-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1824c-113">See also</span></span>

- [<span data-ttu-id="1824c-114">BindingSource Bileşeni</span><span class="sxs-lookup"><span data-stu-id="1824c-114">BindingSource Component</span></span>](bindingsource-component.md)
- [<span data-ttu-id="1824c-115">Nasıl yapılır: Veri Bağlamada Oluşan Hataları ve Özel Durumları İşleme</span><span class="sxs-lookup"><span data-stu-id="1824c-115">How to: Handle Errors and Exceptions that Occur with Databinding</span></span>](how-to-handle-errors-and-exceptions-that-occur-with-databinding.md)
- [<span data-ttu-id="1824c-116">Nasıl yapılır: Windows Forms Denetimini Bir Türe Bağlama</span><span class="sxs-lookup"><span data-stu-id="1824c-116">How to: Bind a Windows Forms Control to a Type</span></span>](how-to-bind-a-windows-forms-control-to-a-type.md)
