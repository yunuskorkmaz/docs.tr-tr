---
title: 'Nasıl yapılır: BindingSource ve INotifyPropertyChanged Arabirimini Kullanarak Değişiklik Bildirimleri Verme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- change notifications [Windows Forms], raising
- BindingSource component [Windows Forms], and IPropertyChange
- data sources [Windows Forms], detecting changes
- examples [Windows Forms], BindingSource component
- change notifications
- INotifyPropertyChanged interface [Windows Forms], using with BindingSource
- BindingSource component [Windows Forms], examples
ms.assetid: 7fa2cf51-c09f-4375-adf0-e36c5617f099
ms.openlocfilehash: 7dc640f272226da650a63b1a3434822d21053b48
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968292"
---
# <a name="how-to-raise-change-notifications-using-a-bindingsource-and-the-inotifypropertychanged-interface"></a><span data-ttu-id="e0861-102">Nasıl yapılır: BindingSource ve INotifyPropertyChanged Arabirimini Kullanarak Değişiklik Bildirimleri Verme</span><span class="sxs-lookup"><span data-stu-id="e0861-102">How to: Raise Change Notifications Using a BindingSource and the INotifyPropertyChanged Interface</span></span>
<span data-ttu-id="e0861-103">Veri kaynağında yer alan tür <xref:System.ComponentModel.INotifyPropertyChanged> Arabirimi uyguladığı ve bir özellik değeri değiştirildiğinde olay harekete geçirirse <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> bileşenbirverikaynağındakideğişiklikleriotomatikolarakalgılar.<xref:System.Windows.Forms.BindingSource></span><span class="sxs-lookup"><span data-stu-id="e0861-103">The <xref:System.Windows.Forms.BindingSource> component will automatically detect changes in a data source when the type contained in the data source implements the <xref:System.ComponentModel.INotifyPropertyChanged> interface and raises <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> events when a property value is changed.</span></span> <span data-ttu-id="e0861-104">Bu, veri kaynağı değerleri değiştikçe, <xref:System.Windows.Forms.BindingSource> ile bağlantılı denetimler otomatik olarak güncelleştirilecek olduğundan kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="e0861-104">This is useful because controls bound to the <xref:System.Windows.Forms.BindingSource> will then automatically update as the data source values change.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e0861-105">Veri kaynağınız uygularsa <xref:System.ComponentModel.INotifyPropertyChanged> ve zaman uyumsuz işlemler gerçekleştiriyorsanız, bir arka plan iş parçacığında veri kaynağında değişiklik yapmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="e0861-105">If your data source implements <xref:System.ComponentModel.INotifyPropertyChanged> and you are performing asynchronous operations, you should not make changes to the data source on a background thread.</span></span> <span data-ttu-id="e0861-106">Bunun yerine, bir arka plan iş parçacığında verileri okumanız ve verileri UI iş parçacığı üzerindeki bir liste ile birleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="e0861-106">Instead, you should read the data on a background thread and merge the data into a list on the UI thread.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e0861-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="e0861-107">Example</span></span>  
 <span data-ttu-id="e0861-108">Aşağıdaki kod örneği, <xref:System.ComponentModel.INotifyPropertyChanged> arabiriminin basit bir uygulamasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e0861-108">The following code example demonstrates a simple implementation of the <xref:System.ComponentModel.INotifyPropertyChanged> interface.</span></span> <span data-ttu-id="e0861-109">Ayrıca, bir veri kaynağı <xref:System.Windows.Forms.BindingSource> değişikliğini, bir <xref:System.ComponentModel.INotifyPropertyChanged> tür listesine bağlandığında, otomatik olarak bir bağlantılı denetime <xref:System.Windows.Forms.BindingSource> nasıl geçireceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="e0861-109">It also shows how the <xref:System.Windows.Forms.BindingSource> automatically passes a data source change to a bound control when the <xref:System.Windows.Forms.BindingSource> is bound to a list of the <xref:System.ComponentModel.INotifyPropertyChanged> type.</span></span>  
  
 <span data-ttu-id="e0861-110">`CallerMemberName` Özniteliğini kullanırsanız `NotifyPropertyChanged` yöntemine yapılan çağrılar, bir dize bağımsız değişkeni olarak özellik adını belirtmek zorunda değildir.</span><span class="sxs-lookup"><span data-stu-id="e0861-110">If you use the `CallerMemberName` attribute, calls to the `NotifyPropertyChanged` method don't have to specify the property name as a string argument.</span></span> <span data-ttu-id="e0861-111">Daha fazla bilgi için bkz. [arayan bilgileriC#()](../../../csharp/programming-guide/concepts/caller-information.md) veya [arayan bilgileri (Visual Basic)](../../../visual-basic/programming-guide/concepts/caller-information.md).</span><span class="sxs-lookup"><span data-stu-id="e0861-111">For more information, see [Caller Information (C#)](../../../csharp/programming-guide/concepts/caller-information.md) or [Caller Information (Visual Basic)](../../../visual-basic/programming-guide/concepts/caller-information.md).</span></span>  
  
 [!code-csharp[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e0861-112">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="e0861-112">Compiling the Code</span></span>  
 <span data-ttu-id="e0861-113">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="e0861-113">This example requires:</span></span>  
  
- <span data-ttu-id="e0861-114">System, System. Data, System. Drawing ve System. Windows. Forms derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="e0861-114">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0861-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e0861-115">See also</span></span>

- <xref:System.ComponentModel.INotifyPropertyChanged>
- [<span data-ttu-id="e0861-116">BindingSource Bileşeni</span><span class="sxs-lookup"><span data-stu-id="e0861-116">BindingSource Component</span></span>](bindingsource-component.md)
- [<span data-ttu-id="e0861-117">Nasıl yapılır: BindingSource ResetItem metodunu kullanarak değişiklik bildirimleri oluştur</span><span class="sxs-lookup"><span data-stu-id="e0861-117">How to: Raise Change Notifications Using the BindingSource ResetItem Method</span></span>](how-to-raise-change-notifications-using-the-bindingsource-resetitem-method.md)
