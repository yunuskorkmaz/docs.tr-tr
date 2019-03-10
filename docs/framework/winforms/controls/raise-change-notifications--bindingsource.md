---
title: 'Nasıl yapılır: BindingSource ve INotifyPropertyChanged arabirimini kullanarak değişiklik bildirimleri Yükselt'
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
ms.openlocfilehash: b637d69556cd96b0cc2ec427527c511d1db2f326
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57707254"
---
# <a name="how-to-raise-change-notifications-using-a-bindingsource-and-the-inotifypropertychanged-interface"></a>Nasıl yapılır: BindingSource ve INotifyPropertyChanged arabirimini kullanarak değişiklik bildirimleri Yükselt
<xref:System.Windows.Forms.BindingSource> Bileşeni otomatik olarak saptar değişiklikleri bir veri kaynağı türü veri kaynağı uygulayan içerdiğinde <xref:System.ComponentModel.INotifyPropertyChanged> arabirimi ve harekete geçirirse <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> bir özellik değeri değiştiğinde olayları. Denetimleri bağlı olduğundan bu yararlıdır <xref:System.Windows.Forms.BindingSource> sonra veri kaynağı değerleri değiştikçe otomatik olarak güncelleştirecektir.  
  
> [!NOTE]
>  Uygular, veri kaynağı, <xref:System.ComponentModel.INotifyPropertyChanged> ve zaman uyumsuz bir işlem gerçekleştiriyorsanız, veri kaynağına bir arka plan iş parçacığı üzerinde değişiklik yapmamalısınız. Bunun yerine, bir arka plan iş parçacığında verileri okumak ve kullanıcı Arabirimi iş parçacığında bir liste verileri birleştirin.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği basit bir uygulamasını gösterir <xref:System.ComponentModel.INotifyPropertyChanged> arabirimi. Ayrıca gösterir nasıl <xref:System.Windows.Forms.BindingSource> otomatik olarak, bir veri kaynağını Değiştir geçirir denetlemek için bir sınır <xref:System.Windows.Forms.BindingSource> listesine bağlı <xref:System.ComponentModel.INotifyPropertyChanged> türü.  
  
 Kullanırsanız `CallerMemberName` özniteliği, çağrıları `NotifyPropertyChanged` yöntem, özellik adını bir dize bağımsız değişkeni belirtmek zorunda değilsiniz. Daha fazla bilgi için [arayan bilgileri (C#)](../../../csharp/programming-guide/concepts/caller-information.md) veya [arayan bilgileri (Visual Basic)](../../../visual-basic/programming-guide/concepts/caller-information.md).  
  
 [!code-csharp[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   Sistem, System.Data System.Drawing ve System.Windows.Forms derlemelere başvuruları.  
  
 Visual Basic veya Visual C# için bu örnek komut satırından derleme hakkında daha fazla bilgi için bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [oluşturma ile komut satırı csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Visual Studio bu örnekte yeni bir projeye kod yapıştırarak da oluşturabilirsiniz. Ayrıca bkz: [nasıl yapılır: Derleme ve Visual Studio kullanarak tam bir Windows Formları kod örneği çalıştırma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb129228(v=vs.100)).  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.ComponentModel.INotifyPropertyChanged>
- [BindingSource Bileşeni](bindingsource-component.md)
- [Nasıl yapılır: BindingSource ve Resetıtem metodunu kullanarak değişiklik bildirimleri Yükselt](how-to-raise-change-notifications-using-the-bindingsource-resetitem-method.md)
