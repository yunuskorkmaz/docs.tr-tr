---
title: 'Nasıl yapılır: BindingSource Bileşenini Kullanarak Bağlı Verileri Formlar Arasında Paylaşma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- examples [Windows Forms], BindingSource component
- data binding [Windows Forms], sharing data across forms
- BindingSource component [Windows Forms], examples
- BindingSource [Windows Forms], using with multiple forms
ms.assetid: a1a49630-db9c-4485-b888-1f62a373a4f7
ms.openlocfilehash: aa497194fd4ac65f48773a45175333a1d862b453
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956068"
---
# <a name="how-to-share-bound-data-across-forms-using-the-bindingsource-component"></a>Nasıl yapılır: BindingSource Bileşenini Kullanarak Bağlı Verileri Formlar Arasında Paylaşma
<xref:System.Windows.Forms.BindingSource> Bileşenini kullanarak formlar arasında kolayca veri paylaşabilirsiniz. Örneğin, veri kaynağı verilerini özetleyen bir salt biçimli form ve veri kaynağında seçili olan öğe hakkında ayrıntılı bilgi içeren başka bir düzenlenebilir form görüntülenmesini isteyebilirsiniz. Bu örnek, bu senaryoyu gösterir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde, bir <xref:System.Windows.Forms.BindingSource> ve onun bağlantılı verilerinin formlar arasında nasıl paylaşılacağını gösterilmektedir. Bu örnekte, paylaşılan <xref:System.Windows.Forms.BindingSource> alt formun oluşturucusuna geçirilir. Alt form, kullanıcının ana formda seçili olan öğenin verilerini düzenlemesini sağlar.  
  
> [!NOTE]
> <xref:System.Windows.Forms.BindingSource> Bileşenin olayı, iki formun eşitlenmiş kalmasını sağlamak için örnekte işlenir. <xref:System.Windows.Forms.BindingSource.BindingComplete> Bunun neden yapıldığı hakkında daha fazla bilgi için bkz [. nasıl yapılır: Aynı veri kaynağıyla bağlantılı birden çok denetimin eşitlenmiş](../multiple-controls-bound-to-data-source-synchronized.md)kalmasını sağlayın.  
  
 [!code-csharp[System.Windows.Forms.BindingSourceMultipleForms#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingSourceMultipleForms/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingSourceMultipleForms#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingSourceMultipleForms/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek şunları gerektirir:  
  
- Sisteme, System. Windows. Forms, System. Drawing, System. Data ve System. xml derlemelerine başvurular.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [BindingSource Bileşeni](bindingsource-component.md)
- [Windows Forms Veri Bağlama](../windows-forms-data-binding.md)
- [Nasıl yapılır: Veri bağlamada oluşan hataları ve özel durumları işleme](how-to-handle-errors-and-exceptions-that-occur-with-databinding.md)
