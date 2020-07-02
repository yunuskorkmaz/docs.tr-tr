---
title: 'Nasıl yapılır: INotifyPropertyChanged Arabirimini Uygulama'
description: Windows Forms veri bağlamasında kullanılan iş nesnelerinde INotifyPropertyChanged arabirimini nasıl uygulayacağınızı öğrenin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- INotifyPropertyChanged interface [Windows Forms], implementing
ms.assetid: eac428af-b43b-46ac-80d9-1a5f88658725
ms.openlocfilehash: 83d2ef32787d2dbcd877bc77dcede10111098f8a
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619274"
---
# <a name="how-to-implement-the-inotifypropertychanged-interface"></a><span data-ttu-id="b5fd4-103">Nasıl yapılır: INotifyPropertyChanged Arabirimini Uygulama</span><span class="sxs-lookup"><span data-stu-id="b5fd4-103">How to: Implement the INotifyPropertyChanged Interface</span></span>
<span data-ttu-id="b5fd4-104">Aşağıdaki kod örneği, arabirimin nasıl uygulanacağını gösterir <xref:System.ComponentModel.INotifyPropertyChanged> .</span><span class="sxs-lookup"><span data-stu-id="b5fd4-104">The following code example demonstrates how to implement the <xref:System.ComponentModel.INotifyPropertyChanged> interface.</span></span> <span data-ttu-id="b5fd4-105">Bu arabirimi Windows Forms veri bağlamasında kullanılan iş nesnelerinde uygulayın.</span><span class="sxs-lookup"><span data-stu-id="b5fd4-105">Implement this interface on business objects that are used in Windows Forms data binding.</span></span> <span data-ttu-id="b5fd4-106">Uygulandığında, arabirim bir iş nesnesindeki Özellik değişiklikleri olan bağlı bir denetime iletişim kurar.</span><span class="sxs-lookup"><span data-stu-id="b5fd4-106">When implemented, the interface  communicates to a bound control the property changes on a business object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b5fd4-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="b5fd4-107">Example</span></span>  
 [!code-csharp[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/VB/Form1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="b5fd4-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b5fd4-108">See also</span></span>

- [<span data-ttu-id="b5fd4-109">Nasıl yapılır: PropertyNameChanged Desenini Uygulama</span><span class="sxs-lookup"><span data-stu-id="b5fd4-109">How to: Apply the PropertyNameChanged Pattern</span></span>](how-to-apply-the-propertynamechanged-pattern.md)
- [<span data-ttu-id="b5fd4-110">Windows Forms Veri Bağlama</span><span class="sxs-lookup"><span data-stu-id="b5fd4-110">Windows Forms Data Binding</span></span>](windows-forms-data-binding.md)
- [<span data-ttu-id="b5fd4-111">Nasıl yapılır: BindingSource ve INotifyPropertyChanged Arabirimini Kullanarak Değişiklik Bildirimleri Verme</span><span class="sxs-lookup"><span data-stu-id="b5fd4-111">How to: Raise Change Notifications Using a BindingSource and the INotifyPropertyChanged Interface</span></span>](./controls/raise-change-notifications--bindingsource.md)
- [<span data-ttu-id="b5fd4-112">Windows Forms Veri Bağlamada Bildirimi Değiştirme</span><span class="sxs-lookup"><span data-stu-id="b5fd4-112">Change Notification in Windows Forms Data Binding</span></span>](change-notification-in-windows-forms-data-binding.md)
