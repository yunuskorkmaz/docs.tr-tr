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
# <a name="how-to-raise-change-notifications-using-a-bindingsource-and-the-inotifypropertychanged-interface"></a>Nasıl yapılır: BindingSource ve INotifyPropertyChanged Arabirimini Kullanarak Değişiklik Bildirimleri Verme
Veri kaynağında yer alan tür <xref:System.ComponentModel.INotifyPropertyChanged> Arabirimi uyguladığı ve bir özellik değeri değiştirildiğinde olay harekete geçirirse <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> bileşenbirverikaynağındakideğişiklikleriotomatikolarakalgılar.<xref:System.Windows.Forms.BindingSource> Bu, veri kaynağı değerleri değiştikçe, <xref:System.Windows.Forms.BindingSource> ile bağlantılı denetimler otomatik olarak güncelleştirilecek olduğundan kullanışlıdır.  
  
> [!NOTE]
> Veri kaynağınız uygularsa <xref:System.ComponentModel.INotifyPropertyChanged> ve zaman uyumsuz işlemler gerçekleştiriyorsanız, bir arka plan iş parçacığında veri kaynağında değişiklik yapmamalıdır. Bunun yerine, bir arka plan iş parçacığında verileri okumanız ve verileri UI iş parçacığı üzerindeki bir liste ile birleştirmeniz gerekir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, <xref:System.ComponentModel.INotifyPropertyChanged> arabiriminin basit bir uygulamasını gösterir. Ayrıca, bir veri kaynağı <xref:System.Windows.Forms.BindingSource> değişikliğini, bir <xref:System.ComponentModel.INotifyPropertyChanged> tür listesine bağlandığında, otomatik olarak bir bağlantılı denetime <xref:System.Windows.Forms.BindingSource> nasıl geçireceğini gösterir.  
  
 `CallerMemberName` Özniteliğini kullanırsanız `NotifyPropertyChanged` yöntemine yapılan çağrılar, bir dize bağımsız değişkeni olarak özellik adını belirtmek zorunda değildir. Daha fazla bilgi için bkz. [arayan bilgileriC#()](../../../csharp/programming-guide/concepts/caller-information.md) veya [arayan bilgileri (Visual Basic)](../../../visual-basic/programming-guide/concepts/caller-information.md).  
  
 [!code-csharp[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek şunları gerektirir:  
  
- System, System. Data, System. Drawing ve System. Windows. Forms derlemelerine başvurular.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ComponentModel.INotifyPropertyChanged>
- [BindingSource Bileşeni](bindingsource-component.md)
- [Nasıl yapılır: BindingSource ResetItem metodunu kullanarak değişiklik bildirimleri oluştur](how-to-raise-change-notifications-using-the-bindingsource-resetitem-method.md)
