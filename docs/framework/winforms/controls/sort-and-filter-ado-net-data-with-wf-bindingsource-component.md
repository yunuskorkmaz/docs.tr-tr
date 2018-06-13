---
title: 'Nasıl yapılır: Windows Forms BindingSource Bileşeni ile ADO.NET Verilerini Sıralama ve Filtreleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sorting data
- data sorting [Windows Forms], ADO.NET
- data [Windows Forms], filtering
- BindingSource component [Windows Forms], sorting and filtering data
- filtering [Windows Forms], ADO.NET
- data [Windows Forms], sorting
- ADO.NET [Windows Forms]
ms.assetid: 6c206daf-d706-4602-9dbe-435343052063
ms.openlocfilehash: 3b58c4f3a53156ab01fb0c0c46b9a9b8d3fea84b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33538080"
---
# <a name="how-to-sort-and-filter-adonet-data-with-the-windows-forms-bindingsource-component"></a>Nasıl yapılır: Windows Forms BindingSource Bileşeni ile ADO.NET Verilerini Sıralama ve Filtreleme
Sıralama ve filtreleme özelliği, getirebilir <xref:System.Windows.Forms.BindingSource> aracılığıyla kontrol <xref:System.Windows.Forms.BindingSource.Sort%2A> ve <xref:System.Windows.Forms.BindingSource.Filter%2A> özellikleri. Temel alınan veri kaynağı olduğunda basit sıralama uygulayabilirsiniz bir <xref:System.ComponentModel.IBindingList>, ve gelişmiş veri kaynağı olduğunda sıralama ve filtreleme uygulayabilirsiniz bir <xref:System.ComponentModel.IBindingListView>. <xref:System.Windows.Forms.BindingSource.Sort%2A> Özelliği gerektiren standart [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] sözdizimi: veri kaynağındaki veri sütununun adını temsil eden bir dize arkasından `ASC` veya `DESC` listeyi artan veya azalan sırada sıralanması olup olmadığını belirtmek için. Gelişmiş sıralama veya her bir sütunun virgülle ayırıcı ile ayırarak birden çok sütun sıralama ayarlayabilirsiniz. <xref:System.Windows.Forms.BindingSource.Filter%2A> Özelliği bir dize ifadesi alır.  
  
> [!NOTE]
>  Bağlantı dizesindeki bir parola gibi hassas bilgileri depolamak, uygulamanızın güvenliğini etkileyebilir. Windows Kimlik Doğrulaması (tümleşik güvenlik olarak da bilinir) kullanılarak bir veritabanına erişimi denetlemek için daha güvenli bir yoldur. Daha fazla bilgi için bkz: [koruma bağlantı bilgilerini](../../../../docs/framework/data/adonet/protecting-connection-information.md).  
  
### <a name="to-filter-data-with-the-bindingsource"></a>BindingSource ile verileri filtrelemek için  
  
-   Ayarlama <xref:System.Windows.Forms.BindingSource.Filter%2A> istediğiniz ifade özelliğine.  
  
     Aşağıdaki kod örneğinde ifade sütunu için istediğiniz değer arkasından bir sütun adı değil.  
  
 [!code-csharp[System.Windows.Forms.DataConnectorFilterAndSort#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/CS/form1.cs#11)]
 [!code-vb[System.Windows.Forms.DataConnectorFilterAndSort#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/VB/form1.vb#11)]  
  
### <a name="to-sort-data-with-the-bindingsource"></a>BindingSource ile verileri sıralama  
  
1.  Ayarlama <xref:System.Windows.Forms.BindingSource.Sort%2A> istediğiniz sütun adından özelliğine `ASC` veya `DESC` artan veya azalan belirtmek için.  
  
2.  Birden çok sütun virgül ile ayırın.  
  
 [!code-csharp[System.Windows.Forms.DataConnectorFilterAndSort#12](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/CS/form1.cs#12)]
 [!code-vb[System.Windows.Forms.DataConnectorFilterAndSort#12](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/VB/form1.vb#12)]  
  
## <a name="example"></a>Örnek  
 Northwind örnek veritabanına Müşteriler tablosundan veri aşağıdaki kod örneğinde yükleyen bir <xref:System.Windows.Forms.DataGridView> denetlemek, filtreleri ve görüntülenen verileri sıralar.  
  
 [!code-csharp[System.Windows.Forms.DataConnectorFilterAndSort#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnectorFilterAndSort#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örneği çalıştırmak için kodu içeren bir forma yapıştırın bir <xref:System.Windows.Forms.BindingSource> adlı `BindingSource1` ve <xref:System.Windows.Forms.DataGridView> adlı `dataGridView1`. İşleme <xref:System.Windows.Forms.Form.Load> çağrısı ve form için olay `InitializeSortedFilteredBindingSource` yük olay işleyicisi yönteminde.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.BindingSource.Sort%2A>  
 <xref:System.Windows.Forms.BindingSource.Filter%2A>  
 [Nasıl yapılır: örnek veritabanları yükleme](http://msdn.microsoft.com/library/ed1291f6-604c-4972-ae22-0345c6dea12e)  
 [BindingSource Bileşeni](../../../../docs/framework/winforms/controls/bindingsource-component.md)
