---
title: 'Nasıl yapılır: INotifyPropertyChanged Arabirimini Uygulama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- INotifyPropertyChanged interface [Windows Forms], implementing
ms.assetid: eac428af-b43b-46ac-80d9-1a5f88658725
ms.openlocfilehash: cfdfb22fd854a8f630243e0f612761c71cb778d8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59225605"
---
# <a name="how-to-implement-the-inotifypropertychanged-interface"></a><span data-ttu-id="ddcfb-102">Nasıl yapılır: INotifyPropertyChanged Arabirimini Uygulama</span><span class="sxs-lookup"><span data-stu-id="ddcfb-102">How to: Implement the INotifyPropertyChanged Interface</span></span>
<span data-ttu-id="ddcfb-103">Aşağıdaki kod örneğinde nasıl uygulanacağını gösterir <xref:System.ComponentModel.INotifyPropertyChanged> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="ddcfb-103">The following code example demonstrates how to implement the <xref:System.ComponentModel.INotifyPropertyChanged> interface.</span></span> <span data-ttu-id="ddcfb-104">Windows Forms veri bağlamada kullanılan iş nesneler üzerinde bu arabirimi uygulayın.</span><span class="sxs-lookup"><span data-stu-id="ddcfb-104">Implement this interface on business objects that are used in Windows Forms data binding.</span></span> <span data-ttu-id="ddcfb-105">Arabirim uygulandığında, ilişkili bir denetim için bir iş nesnesi üzerinde özellik değişikliklerinin iletişim kurar.</span><span class="sxs-lookup"><span data-stu-id="ddcfb-105">When implemented, the interface  communicates to a bound control the property changes on a business object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ddcfb-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="ddcfb-106">Example</span></span>  
 [!code-csharp[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/VB/Form1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="ddcfb-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ddcfb-107">See also</span></span>

- [<span data-ttu-id="ddcfb-108">Nasıl yapılır: PropertyNameChanged desenini uygulama</span><span class="sxs-lookup"><span data-stu-id="ddcfb-108">How to: Apply the PropertyNameChanged Pattern</span></span>](how-to-apply-the-propertynamechanged-pattern.md)
- [<span data-ttu-id="ddcfb-109">Windows Forms Veri Bağlama</span><span class="sxs-lookup"><span data-stu-id="ddcfb-109">Windows Forms Data Binding</span></span>](windows-forms-data-binding.md)
- [<span data-ttu-id="ddcfb-110">Nasıl yapılır: BindingSource ve INotifyPropertyChanged arabirimini kullanarak değişiklik bildirimleri Yükselt</span><span class="sxs-lookup"><span data-stu-id="ddcfb-110">How to: Raise Change Notifications Using a BindingSource and the INotifyPropertyChanged Interface</span></span>](./controls/raise-change-notifications--bindingsource.md)
- [<span data-ttu-id="ddcfb-111">Windows Forms Veri Bağlamada Bildirimi Değiştirme</span><span class="sxs-lookup"><span data-stu-id="ddcfb-111">Change Notification in Windows Forms Data Binding</span></span>](change-notification-in-windows-forms-data-binding.md)
