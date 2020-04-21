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
ms.openlocfilehash: 2fe4458aa43144a9c29ed67fd7bee99a37fe1434
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81739690"
---
# <a name="how-to-raise-change-notifications-using-a-bindingsource-and-the-inotifypropertychanged-interface"></a><span data-ttu-id="84cda-102">Nasıl yapılır: BindingSource ve INotifyPropertyChanged Arabirimini Kullanarak Değişiklik Bildirimleri Verme</span><span class="sxs-lookup"><span data-stu-id="84cda-102">How to: Raise Change Notifications Using a BindingSource and the INotifyPropertyChanged Interface</span></span>
<span data-ttu-id="84cda-103">Bileşen, <xref:System.Windows.Forms.BindingSource> veri kaynağında bulunan tür bir özellik değeri değiştirildiğinde <xref:System.ComponentModel.INotifyPropertyChanged> olayları <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> uyguladığında ve yükselttiğinde, veri kaynağındaki değişiklikleri otomatik olarak algılar.</span><span class="sxs-lookup"><span data-stu-id="84cda-103">The <xref:System.Windows.Forms.BindingSource> component automatically detects changes in a data source when the type contained in the data source implements <xref:System.ComponentModel.INotifyPropertyChanged> and raises <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> events when a property value is changed.</span></span> <span data-ttu-id="84cda-104">Veri kaynağı değerleri değiştikçe <xref:System.Windows.Forms.BindingSource> otomatik olarak güncelleştirmeye bağlı denetimler nedeniyle bu değişiklik algılaması yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="84cda-104">This change detection is useful because controls bound to the <xref:System.Windows.Forms.BindingSource> automatically update as the data source values change.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="84cda-105">Veri kaynağınız uygular <xref:System.ComponentModel.INotifyPropertyChanged> ve eşzamanlı işlemler gerçekleştirmektedirseniz, arka plan iş parçacığındaki veri kaynağında değişiklik yapmamalısınız.</span><span class="sxs-lookup"><span data-stu-id="84cda-105">If your data source implements <xref:System.ComponentModel.INotifyPropertyChanged> and you are performing asynchronous operations, you should not make changes to the data source on a background thread.</span></span> <span data-ttu-id="84cda-106">Bunun yerine, bir arka plan iş parçacığı üzerindeki verileri okumanız ve verileri UI iş parçacığındaki bir listede birleştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="84cda-106">Instead, you should read the data on a background thread and merge the data into a list on the UI thread.</span></span>  
  
## <a name="example"></a><span data-ttu-id="84cda-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="84cda-107">Example</span></span>  
 <span data-ttu-id="84cda-108">Aşağıdaki kod <xref:System.ComponentModel.INotifyPropertyChanged> örneği, arabirimin basit bir uygulamasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="84cda-108">The following code example demonstrates a simple implementation of the <xref:System.ComponentModel.INotifyPropertyChanged> interface.</span></span> <span data-ttu-id="84cda-109">Ayrıca, bir <xref:System.Windows.Forms.BindingSource> veri kaynağının <xref:System.ComponentModel.INotifyPropertyChanged> türünün listesine bağlandığında <xref:System.Windows.Forms.BindingSource> bağlı bir denetime nasıl otomatik olarak geçtiğini de gösterir.</span><span class="sxs-lookup"><span data-stu-id="84cda-109">It also shows how the <xref:System.Windows.Forms.BindingSource> automatically passes a data source change to a bound control when the <xref:System.Windows.Forms.BindingSource> is bound to a list of the <xref:System.ComponentModel.INotifyPropertyChanged> type.</span></span>  
  
 <span data-ttu-id="84cda-110">`CallerMemberName` Öznitelik kullanırsanız, `NotifyPropertyChanged` yönteme yapılan çağrıların özellik adını dize bağımsız değişkeni olarak belirtmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="84cda-110">If you use the `CallerMemberName` attribute, calls to the `NotifyPropertyChanged` method don't have to specify the property name as a string argument.</span></span> <span data-ttu-id="84cda-111">Daha fazla bilgi için [Bkz. Arayan Bilgileri (C#)](../../../csharp/language-reference/attributes/caller-information.md) veya [Arayan Bilgileri (Visual Basic)](../../../visual-basic/programming-guide/concepts/caller-information.md).</span><span class="sxs-lookup"><span data-stu-id="84cda-111">For more information, see [Caller Information (C#)](../../../csharp/language-reference/attributes/caller-information.md) or [Caller Information (Visual Basic)](../../../visual-basic/programming-guide/concepts/caller-information.md).</span></span>  
  
 [!code-csharp[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="84cda-112">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="84cda-112">Compiling the Code</span></span>  
 <span data-ttu-id="84cda-113">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="84cda-113">This example requires:</span></span>  
  
- <span data-ttu-id="84cda-114">Sistem, System.Data, System.Drawing ve System.Windows.Forms derlemelerine yapılan atıflar.</span><span class="sxs-lookup"><span data-stu-id="84cda-114">References to the System, System.Data, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84cda-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="84cda-115">See also</span></span>

- <xref:System.ComponentModel.INotifyPropertyChanged>
- [<span data-ttu-id="84cda-116">BindingSource Bileşeni</span><span class="sxs-lookup"><span data-stu-id="84cda-116">BindingSource Component</span></span>](bindingsource-component.md)
- [<span data-ttu-id="84cda-117">Nasıl yapılır: BindingSource ve ResetItem Metodunu Kullanarak Değişiklik Bildirimleri Verme</span><span class="sxs-lookup"><span data-stu-id="84cda-117">How to: Raise Change Notifications Using the BindingSource ResetItem Method</span></span>](how-to-raise-change-notifications-using-the-bindingsource-resetitem-method.md)
