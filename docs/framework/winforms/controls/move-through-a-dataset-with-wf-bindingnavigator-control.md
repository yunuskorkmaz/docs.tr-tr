---
title: 'Nasıl yapılır: Windows Forms BindingNavigator Denetimi ile DataSet içinde Hareket Etme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- datasets [Windows Forms], moving through
- BindingNavigator control [Windows Forms], moving through datasets
- examples [Windows Forms], BindingNavigator control
ms.assetid: 146d97be-3d97-400e-accb-860bbf47729d
ms.openlocfilehash: d33cad4d0a60aa29d8c9f5e2217532963e8358c4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69952690"
---
# <a name="how-to-move-through-a-dataset-with-the-windows-forms-bindingnavigator-control"></a>Nasıl yapılır: Windows Forms BindingNavigator Denetimi ile DataSet içinde Hareket Etme
Veri odaklı uygulamalar oluştururken, genellikle kullanıcılara veri koleksiyonlarını görüntülemesi gerekir. <xref:System.Windows.Forms.BindingSource> Bileşeniyle birlikte denetim, bir koleksiyon içinde gezinmek ve öğeleri sıralı olarak görüntülemek için uygun ve Genişletilebilir <xref:System.Windows.Forms.BindingNavigator> bir çözüm sağlar.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, verilerin nasıl taşınacağı hakkında bir <xref:System.Windows.Forms.BindingNavigator> denetimin nasıl kullanılacağını göstermektedir. Küme, <xref:System.Data.DataView> bileşeni<xref:System.Windows.Forms.BindingSource> olan bir <xref:System.Windows.Forms.TextBox> denetime bağlantılı olan ' de bulunur.  
  
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
- [Nasıl yapılır: Windows Forms denetimini bir türe bağlama](how-to-bind-a-windows-forms-control-to-a-type.md)
