---
title: "Nasıl yapılır: INotifyPropertyChanged Arabirimini Uygulama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: INotifyPropertyChanged interface [Windows Forms], implementing
ms.assetid: eac428af-b43b-46ac-80d9-1a5f88658725
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 54dc436ec40f001ab1bf90acaedf22745d35d1b4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-implement-the-inotifypropertychanged-interface"></a><span data-ttu-id="d9946-102">Nasıl yapılır: INotifyPropertyChanged Arabirimini Uygulama</span><span class="sxs-lookup"><span data-stu-id="d9946-102">How to: Implement the INotifyPropertyChanged Interface</span></span>
<span data-ttu-id="d9946-103">Aşağıdaki kod örneğinde nasıl uygulanacağını gösterilen <xref:System.ComponentModel.INotifyPropertyChanged> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="d9946-103">The following code example demonstrates how to implement the <xref:System.ComponentModel.INotifyPropertyChanged> interface.</span></span> <span data-ttu-id="d9946-104">Windows Forms veri bağlamada kullanılan iş nesneler üzerinde bu arabirimi uygular.</span><span class="sxs-lookup"><span data-stu-id="d9946-104">Implement this interface on business objects that are used in Windows Forms data binding.</span></span> <span data-ttu-id="d9946-105">Uygulandığında, arabirim ilişkili bir denetim için bir iş nesnesi üzerinde özellik değişikliklerini iletişim kurar.</span><span class="sxs-lookup"><span data-stu-id="d9946-105">When implemented, the interface  communicates to a bound control the property changes on a business object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d9946-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="d9946-106">Example</span></span>  
 [!code-csharp[System.ComponentModel.IPropertyChangeExample#1](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.IPropertyChangeExample#1](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/VB/Form1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="d9946-107">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d9946-107">See Also</span></span>  
 [<span data-ttu-id="d9946-108">Nasıl yapılır: PropertyNameChanged desenini uygulama</span><span class="sxs-lookup"><span data-stu-id="d9946-108">How to: Apply the PropertyNameChanged Pattern</span></span>](../../../docs/framework/winforms/how-to-apply-the-propertynamechanged-pattern.md)  
 [<span data-ttu-id="d9946-109">Windows Forms veri bağlama</span><span class="sxs-lookup"><span data-stu-id="d9946-109">Windows Forms Data Binding</span></span>](../../../docs/framework/winforms/windows-forms-data-binding.md)  
 [<span data-ttu-id="d9946-110">Nasıl yapılır: BindingSource ve INotifyPropertyChanged arabirimini kullanarak değişiklik bildirimleri</span><span class="sxs-lookup"><span data-stu-id="d9946-110">How to: Raise Change Notifications Using a BindingSource and the INotifyPropertyChanged Interface</span></span>](../../../docs/framework/winforms/controls/raise-change-notifications--bindingsource.md)  
 [<span data-ttu-id="d9946-111">Windows Forms veri bağlamada bildirimi değiştirme</span><span class="sxs-lookup"><span data-stu-id="d9946-111">Change Notification in Windows Forms Data Binding</span></span>](../../../docs/framework/winforms/change-notification-in-windows-forms-data-binding.md)
