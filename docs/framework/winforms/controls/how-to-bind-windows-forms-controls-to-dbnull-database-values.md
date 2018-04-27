---
title: 'Nasıl yapılır: Windows Forms Denetimlerini DBNull Veritabanı Değerlerine Bağlama'
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
- BindingSource component [Windows Forms], binding to DBNull values
- examples [Windows Forms], BindingSource component
- controls [Windows Forms], binding to DBNull values
ms.assetid: 96494e6f-5f40-4f83-af97-bbd7192c2af8
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 45bfed3020f0fe148e9f7d33b9ec7dc243eb5c29
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-bind-windows-forms-controls-to-dbnull-database-values"></a>Nasıl yapılır: Windows Forms Denetimlerini DBNull Veritabanı Değerlerine Bağlama
Bir veri kaynağı ve veri kaynağı için Windows Forms denetimleri bağladığınızda döndüren bir <xref:System.DBNull> değeri, yerine uygun değeri işleme, biçimlendirme veya olayları ayrıştırma olmadan. <xref:System.Windows.Forms.Binding.NullValue%2A> Özelliği tarafından dönüştürülür <xref:System.DBNull> biçimlendirme veya veri kaynağı değerlerini ayrıştırma belirtilen bir nesneye.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte nasıl bağlanacağını gösterir bir <xref:System.DBNull> iki farklı durumlarda değeri. İlk nasıl ayarlanacağını gösterir <xref:System.Windows.Forms.Binding.NullValue%2A> dizesi özelliği için; ikinci nasıl ayarlanacağını gösterir. <xref:System.Windows.Forms.Binding.NullValue%2A> bir görüntü özelliği için.  
  
 [!code-csharp[System.Windows.Forms.BindingDBNull#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingDBNull/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingDBNull#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingDBNull/VB/form1.vb#1)]  
  
 Bağlı özellik türleri ve <xref:System.Windows.Forms.Binding.NullValue%2A> özelliği aynı olması gerekir veya bir hata neden olacak ve daha fazla <xref:System.Windows.Forms.Binding.NullValue%2A> değerleri işlenmeyecek. Bu durumda, bir özel durum değil.  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   Sistem, System.Data, System.Drawing ve System.Windows.Forms derlemelerine başvurular.  
  
 Visual Basic veya Visual C# için bu örnek komut satırından oluşturma hakkında daha fazla bilgi için bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [komut satırı derleme ile csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Bu örnek Visual Studio'da yeni bir projeye kod yapıştırılarak de oluşturabilirsiniz.  Ayrıca bkz. [nasıl yapılır: derleme ve çalıştırma bir tam Windows Forms kod örneği kullanarak Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [BindingSource Bileşeni](../../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [Nasıl yapılır: Veri Bağlamada Oluşan Hataları ve Özel Durumları İşleme](../../../../docs/framework/winforms/controls/how-to-handle-errors-and-exceptions-that-occur-with-databinding.md)  
 [Nasıl yapılır: Windows Forms Denetimini Bir Türe Bağlama](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)
