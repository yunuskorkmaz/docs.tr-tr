---
title: BindingSource bileşeniyle ADO.NET verilerini sıralama ve filtreleme
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
ms.openlocfilehash: cf1da3bb94b26449eb72b0e4930b262236487acc
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742966"
---
# <a name="how-to-sort-and-filter-adonet-data-with-the-windows-forms-bindingsource-component"></a>Nasıl yapılır: Windows Forms BindingSource Bileşeni ile ADO.NET Verilerini Sıralama ve Filtreleme
<xref:System.Windows.Forms.BindingSource> denetimin sıralama ve filtreleme özelliğini <xref:System.Windows.Forms.BindingSource.Sort%2A> ve <xref:System.Windows.Forms.BindingSource.Filter%2A> özellikleriyle kullanıma sunabilirsiniz. Temel alınan veri kaynağı bir <xref:System.ComponentModel.IBindingList>olduğunda basit sıralama uygulayabilir ve veri kaynağı bir <xref:System.ComponentModel.IBindingListView>olduğunda filtreleme ve gelişmiş sıralama uygulayabilirsiniz. <xref:System.Windows.Forms.BindingSource.Sort%2A> özelliği için standart ADO.NET sözdizimi gerekir: veri kaynağındaki bir veri sütununun adını temsil eden bir dize ve sonra listenin artan veya azalan sırada sıralanması gerekip gerekmediğini belirtmek için `ASC` veya `DESC`. Her sütunu virgül ayırıcısıyla ayırarak gelişmiş sıralama veya birden çok sütunlu sıralama ayarlayabilirsiniz. <xref:System.Windows.Forms.BindingSource.Filter%2A> özelliği bir dize ifadesi alır.  
  
> [!NOTE]
> Parola gibi hassas bilgileri, bağlantı dizesi içinde depolamak, uygulamanızın güvenliğini etkileyebilir. Windows Kimlik Doğrulaması (tümleşik güvenlik olarak da bilinir) kullanılarak bir veritabanına erişimi denetlemek için daha güvenli bir yoldur. Daha fazla bilgi için bkz. [bağlantı bilgilerini koruma](../../data/adonet/protecting-connection-information.md).  
  
### <a name="to-filter-data-with-the-bindingsource"></a>BindingSource ile verileri filtrelemek için  
  
- <xref:System.Windows.Forms.BindingSource.Filter%2A> özelliğini istediğiniz ifadeye ayarlayın.  
  
     Aşağıdaki kod örneğinde, ifadesi bir sütun adı ve ardından sütun için istediğiniz değeri izler.  
  
 [!code-csharp[System.Windows.Forms.DataConnectorFilterAndSort#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/CS/form1.cs#11)]
 [!code-vb[System.Windows.Forms.DataConnectorFilterAndSort#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/VB/form1.vb#11)]  
  
### <a name="to-sort-data-with-the-bindingsource"></a>BindingSource ile verileri sıralamak için  
  
1. <xref:System.Windows.Forms.BindingSource.Sort%2A> özelliğini, ardından `ASC` veya `DESC` artan veya azalan sırada göstermek için istediğiniz sütun adı olarak ayarlayın.  
  
2. Birden çok sütunu virgülle ayırın.  
  
 [!code-csharp[System.Windows.Forms.DataConnectorFilterAndSort#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/CS/form1.cs#12)]
 [!code-vb[System.Windows.Forms.DataConnectorFilterAndSort#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/VB/form1.vb#12)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, Northwind örnek veritabanının Customers tablosundaki verileri bir <xref:System.Windows.Forms.DataGridView> denetimine yükler ve görünen verileri filtreleyerek sıralar.  
  
 [!code-csharp[System.Windows.Forms.DataConnectorFilterAndSort#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnectorFilterAndSort#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örneği çalıştırmak için kodu, `BindingSource1` adlı bir <xref:System.Windows.Forms.BindingSource> ve `dataGridView1`adlı <xref:System.Windows.Forms.DataGridView> içeren bir forma yapıştırın. Form için <xref:System.Windows.Forms.Form.Load> olayını işleyin ve Load olay işleyicisi yönteminde `InitializeSortedFilteredBindingSource` çağırın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.BindingSource.Sort%2A>
- <xref:System.Windows.Forms.BindingSource.Filter%2A>
- [Nasıl yapılır: örnek veritabanları yüklemesi](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/8b6y4c7s(v=vs.120))
- [BindingSource Bileşeni](bindingsource-component.md)
