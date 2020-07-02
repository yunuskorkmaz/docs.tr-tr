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
# <a name="how-to-implement-the-inotifypropertychanged-interface"></a>Nasıl yapılır: INotifyPropertyChanged Arabirimini Uygulama
Aşağıdaki kod örneği, arabirimin nasıl uygulanacağını gösterir <xref:System.ComponentModel.INotifyPropertyChanged> . Bu arabirimi Windows Forms veri bağlamasında kullanılan iş nesnelerinde uygulayın. Uygulandığında, arabirim bir iş nesnesindeki Özellik değişiklikleri olan bağlı bir denetime iletişim kurar.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/VB/Form1.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: PropertyNameChanged Desenini Uygulama](how-to-apply-the-propertynamechanged-pattern.md)
- [Windows Forms Veri Bağlama](windows-forms-data-binding.md)
- [Nasıl yapılır: BindingSource ve INotifyPropertyChanged Arabirimini Kullanarak Değişiklik Bildirimleri Verme](./controls/raise-change-notifications--bindingsource.md)
- [Windows Forms Veri Bağlamada Bildirimi Değiştirme](change-notification-in-windows-forms-data-binding.md)
