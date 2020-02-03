---
title: BindingNavigator denetimiyle bir veri kümesi Içinde geçiş yapın
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- datasets [Windows Forms], moving through
- BindingNavigator control [Windows Forms], moving through datasets
- examples [Windows Forms], BindingNavigator control
ms.assetid: 146d97be-3d97-400e-accb-860bbf47729d
ms.openlocfilehash: 73a102da74a3a2a00b5042331cffcaf3d858ea5b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742158"
---
# <a name="how-to-move-through-a-dataset-with-the-windows-forms-bindingnavigator-control"></a>Nasıl yapılır: Windows Forms BindingNavigator Denetimi ile DataSet içinde Hareket Etme
Veri odaklı uygulamalar oluştururken, genellikle kullanıcılara veri koleksiyonlarını görüntülemesi gerekir. <xref:System.Windows.Forms.BindingSource> bileşeniyle birlikte <xref:System.Windows.Forms.BindingNavigator> denetimi, bir koleksiyon içinde gezinmek ve öğeleri sıralı olarak görüntülemek için uygun ve genişletilebilir bir çözüm sunar.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, veri üzerinden geçmek için <xref:System.Windows.Forms.BindingNavigator> denetimini nasıl kullanacağınızı gösterir. Küme, bir <xref:System.Windows.Forms.BindingSource> bileşeniyle <xref:System.Windows.Forms.TextBox> denetimine bağlantılı olan bir <xref:System.Data.DataView>bulunur.  
  
> [!NOTE]
> Parola gibi hassas bilgileri, bağlantı dizesi içinde depolamak, uygulamanızın güvenliğini etkileyebilir. Windows Kimlik Doğrulaması (tümleşik güvenlik olarak da bilinir) kullanılarak bir veritabanına erişimi denetlemek için daha güvenli bir yoldur. Daha fazla bilgi için bkz. [bağlantı bilgilerini koruma](../../data/adonet/protecting-connection-information.md).  
  
 [!code-csharp[System.Windows.Forms.DataNavigator#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataNavigator/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataNavigator#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataNavigator/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek şunları gerektirir:  
  
- System, System. Data, System. Drawing, System. Windows. Forms ve System. xml derlemelerine başvuru.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [BindingNavigator Denetimi](bindingnavigator-control-windows-forms.md)
- [BindingSource Bileşeni](bindingsource-component.md)
- [Nasıl yapılır: Windows Forms Denetimini Bir Türe Bağlama](how-to-bind-a-windows-forms-control-to-a-type.md)
