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
# <a name="how-to-raise-change-notifications-using-a-bindingsource-and-the-inotifypropertychanged-interface"></a>Nasıl yapılır: BindingSource ve INotifyPropertyChanged Arabirimini Kullanarak Değişiklik Bildirimleri Verme
Bileşen, <xref:System.Windows.Forms.BindingSource> veri kaynağında bulunan tür bir özellik değeri değiştirildiğinde <xref:System.ComponentModel.INotifyPropertyChanged> olayları <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> uyguladığında ve yükselttiğinde, veri kaynağındaki değişiklikleri otomatik olarak algılar. Veri kaynağı değerleri değiştikçe <xref:System.Windows.Forms.BindingSource> otomatik olarak güncelleştirmeye bağlı denetimler nedeniyle bu değişiklik algılaması yararlıdır.  
  
> [!NOTE]
> Veri kaynağınız uygular <xref:System.ComponentModel.INotifyPropertyChanged> ve eşzamanlı işlemler gerçekleştirmektedirseniz, arka plan iş parçacığındaki veri kaynağında değişiklik yapmamalısınız. Bunun yerine, bir arka plan iş parçacığı üzerindeki verileri okumanız ve verileri UI iş parçacığındaki bir listede birleştirmeniz gerekir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod <xref:System.ComponentModel.INotifyPropertyChanged> örneği, arabirimin basit bir uygulamasını gösterir. Ayrıca, bir <xref:System.Windows.Forms.BindingSource> veri kaynağının <xref:System.ComponentModel.INotifyPropertyChanged> türünün listesine bağlandığında <xref:System.Windows.Forms.BindingSource> bağlı bir denetime nasıl otomatik olarak geçtiğini de gösterir.  
  
 `CallerMemberName` Öznitelik kullanırsanız, `NotifyPropertyChanged` yönteme yapılan çağrıların özellik adını dize bağımsız değişkeni olarak belirtmeniz gerekmez. Daha fazla bilgi için [Bkz. Arayan Bilgileri (C#)](../../../csharp/language-reference/attributes/caller-information.md) veya [Arayan Bilgileri (Visual Basic)](../../../visual-basic/programming-guide/concepts/caller-information.md).  
  
 [!code-csharp[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek şunları gerektirir:  
  
- Sistem, System.Data, System.Drawing ve System.Windows.Forms derlemelerine yapılan atıflar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ComponentModel.INotifyPropertyChanged>
- [BindingSource Bileşeni](bindingsource-component.md)
- [Nasıl yapılır: BindingSource ve ResetItem Metodunu Kullanarak Değişiklik Bildirimleri Verme](how-to-raise-change-notifications-using-the-bindingsource-resetitem-method.md)
