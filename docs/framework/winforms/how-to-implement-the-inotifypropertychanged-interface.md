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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59225605"
---
# <a name="how-to-implement-the-inotifypropertychanged-interface"></a><span data-ttu-id="56d13-102">Nasıl yapılır: INotifyPropertyChanged Arabirimini Uygulama</span><span class="sxs-lookup"><span data-stu-id="56d13-102">How to: Implement the INotifyPropertyChanged Interface</span></span>
<span data-ttu-id="56d13-103">Aşağıdaki kod örneğinde nasıl uygulanacağını gösterir <xref:System.ComponentModel.INotifyPropertyChanged> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="56d13-103">The following code example demonstrates how to implement the <xref:System.ComponentModel.INotifyPropertyChanged> interface.</span></span> <span data-ttu-id="56d13-104">Windows Forms veri bağlamada kullanılan iş nesneler üzerinde bu arabirimi uygulayın.</span><span class="sxs-lookup"><span data-stu-id="56d13-104">Implement this interface on business objects that are used in Windows Forms data binding.</span></span> <span data-ttu-id="56d13-105">Arabirim uygulandığında, ilişkili bir denetim için bir iş nesnesi üzerinde özellik değişikliklerinin iletişim kurar.</span><span class="sxs-lookup"><span data-stu-id="56d13-105">When implemented, the interface  communicates to a bound control the property changes on a business object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="56d13-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="56d13-106">Example</span></span>  
 [!code-csharp[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/VB/Form1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="56d13-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="56d13-107">See also</span></span>

- [<span data-ttu-id="56d13-108">Nasıl yapılır: PropertyNameChanged Desenini Uygulama</span><span class="sxs-lookup"><span data-stu-id="56d13-108">How to: Apply the PropertyNameChanged Pattern</span></span>](how-to-apply-the-propertynamechanged-pattern.md)
- [<span data-ttu-id="56d13-109">Windows Forms Veri Bağlama</span><span class="sxs-lookup"><span data-stu-id="56d13-109">Windows Forms Data Binding</span></span>](windows-forms-data-binding.md)
- [<span data-ttu-id="56d13-110">Nasıl yapılır: BindingSource ve INotifyPropertyChanged Arabirimini Kullanarak Değişiklik Bildirimleri Verme</span><span class="sxs-lookup"><span data-stu-id="56d13-110">How to: Raise Change Notifications Using a BindingSource and the INotifyPropertyChanged Interface</span></span>](./controls/raise-change-notifications--bindingsource.md)
- [<span data-ttu-id="56d13-111">Windows Forms Veri Bağlamada Bildirimi Değiştirme</span><span class="sxs-lookup"><span data-stu-id="56d13-111">Change Notification in Windows Forms Data Binding</span></span>](change-notification-in-windows-forms-data-binding.md)
