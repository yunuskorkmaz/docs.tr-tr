---
title: 'Nasıl yapılır: BindingSource ve INotifyPropertyChanged Arabirimini Kullanarak Değişiklik Bildirimleri Verme'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: de75d4d3d8de34bc85ee47b6761724da93fc0ecc
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-raise-change-notifications-using-a-bindingsource-and-the-inotifypropertychanged-interface"></a>Nasıl yapılır: BindingSource ve INotifyPropertyChanged Arabirimini Kullanarak Değişiklik Bildirimleri Verme
<xref:System.Windows.Forms.BindingSource> Bileşen otomatik olarak saptar değişiklikleri bir veri kaynağı türü, veri kaynağı uygular, bağımsız <xref:System.ComponentModel.INotifyPropertyChanged> arabirimi ve başlatır <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> bir özellik değeri değiştiğinde olaylar. Denetimlerin bağlı olduğundan bu işlem faydalı olur <xref:System.Windows.Forms.BindingSource> sonra veri kaynağı değerleri değiştikçe otomatik olarak güncelleştirir.  
  
> [!NOTE]
>  Implements, veri kaynağı, <xref:System.ComponentModel.INotifyPropertyChanged> ve zaman uyumsuz işlemleri gerçekleştiren, arka plan iş parçacığında veri kaynağına değişiklik yapmamalısınız. Bunun yerine, arka plan iş parçacığında verileri okumak ve kullanıcı Arabirimi iş parçacığı listede verileri birleştirin.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde basit bir uygulama ortaya koyar <xref:System.ComponentModel.INotifyPropertyChanged> arabirimi. Ayrıca gösterir nasıl <xref:System.Windows.Forms.BindingSource> otomatik olarak, bir veri kaynağı değişikliği geçirir denetlemek için bir sınır <xref:System.Windows.Forms.BindingSource> listesine bağlı <xref:System.ComponentModel.INotifyPropertyChanged> türü.  
  
 Kullanırsanız `CallerMemberName` özniteliği, çağrıları `NotifyPropertyChanged` yöntemi dize bağımsız değişkeni özellik adını belirtmek zorunda değilsiniz. Daha fazla bilgi için bkz: [arayan bilgileri](http://msdn.microsoft.com/library/9cb2b8c0-c4f6-44b8-9c90-38948455b373).  
  
 [!code-csharp[System.ComponentModel.IPropertyChangeExample#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.IPropertyChangeExample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   Sistem, System.Data, System.Drawing ve System.Windows.Forms derlemelerine başvurular.  
  
 Visual Basic veya Visual C# için bu örnek komut satırından oluşturma hakkında daha fazla bilgi için bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [komut satırı derleme ile csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Bu örnek Visual Studio'da yeni bir projeye kod yapıştırılarak de oluşturabilirsiniz.  Ayrıca bkz. [HYPERLINK "http://msdn.microsoft.com/library/Bb129228(v=vs.110)" nasıl yapılır: derleme ve çalıştırma bir tam Windows Forms kod örneği kullanarak Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ComponentModel.INotifyPropertyChanged>  
 [BindingSource Bileşeni](../../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [Nasıl yapılır: BindingSource ve ResetItem Metodunu Kullanarak Değişiklik Bildirimleri Verme](../../../../docs/framework/winforms/controls/how-to-raise-change-notifications-using-the-bindingsource-resetitem-method.md)
