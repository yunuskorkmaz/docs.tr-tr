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
ms.openlocfilehash: ae331ca9e3fd2aed654659e11434454874eff8fa
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960420"
---
# <a name="how-to-sort-and-filter-adonet-data-with-the-windows-forms-bindingsource-component"></a>Nasıl yapılır: Windows Forms BindingSource Bileşeni ile ADO.NET Verilerini Sıralama ve Filtreleme
Ve<xref:System.Windows.Forms.BindingSource.Sort%2A> <xref:System.Windows.Forms.BindingSource> özellikleriiledenetiminsıralamavefiltreleme<xref:System.Windows.Forms.BindingSource.Filter%2A> özelliğini kullanıma sunabilirsiniz. Temel alınan veri kaynağı bir <xref:System.ComponentModel.IBindingList>olduğunda basit sıralama uygulayabilir ve veri kaynağı bir <xref:System.ComponentModel.IBindingListView>olduğunda filtreleme ve gelişmiş sıralama uygulayabilirsiniz. Özelliği için standart ADO.NET sözdizimi gerekir: veri kaynağındaki bir veri sütununun adını temsil eden bir dize ve `ASC` sonra `DESC` listenin artan veya azalan sırada sıralanması gerekip gerekmediğini belirtmek için. <xref:System.Windows.Forms.BindingSource.Sort%2A> Her sütunu virgül ayırıcısıyla ayırarak gelişmiş sıralama veya birden çok sütunlu sıralama ayarlayabilirsiniz. <xref:System.Windows.Forms.BindingSource.Filter%2A> Özelliği bir dize ifadesi alır.  
  
> [!NOTE]
> Parola gibi hassas bilgileri, bağlantı dizesi içinde depolamak, uygulamanızın güvenliğini etkileyebilir. Windows Kimlik Doğrulaması (tümleşik güvenlik olarak da bilinir) kullanılarak bir veritabanına erişimi denetlemek için daha güvenli bir yoldur. Daha fazla bilgi için bkz. [bağlantı bilgilerini koruma](../../data/adonet/protecting-connection-information.md).  
  
### <a name="to-filter-data-with-the-bindingsource"></a>BindingSource ile verileri filtrelemek için  
  
- <xref:System.Windows.Forms.BindingSource.Filter%2A> Özelliğini istediğiniz ifadeye ayarlayın.  
  
     Aşağıdaki kod örneğinde, ifadesi bir sütun adı ve ardından sütun için istediğiniz değeri izler.  
  
 [!code-csharp[System.Windows.Forms.DataConnectorFilterAndSort#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/CS/form1.cs#11)]
 [!code-vb[System.Windows.Forms.DataConnectorFilterAndSort#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/VB/form1.vb#11)]  
  
### <a name="to-sort-data-with-the-bindingsource"></a>BindingSource ile verileri sıralamak için  
  
1. Özelliğini, daha `ASC` sonra istediğiniz sütun adı olarak ayarlayın veya `DESC` artan veya azalan sırayı belirtin. <xref:System.Windows.Forms.BindingSource.Sort%2A>  
  
2. Birden çok sütunu virgülle ayırın.  
  
 [!code-csharp[System.Windows.Forms.DataConnectorFilterAndSort#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/CS/form1.cs#12)]
 [!code-vb[System.Windows.Forms.DataConnectorFilterAndSort#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/VB/form1.vb#12)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, verileri Northwind örnek veritabanının Customers tablosundan bir <xref:System.Windows.Forms.DataGridView> denetime yükler ve görünen verileri filtreler ve sıralar.  
  
 [!code-csharp[System.Windows.Forms.DataConnectorFilterAndSort#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnectorFilterAndSort#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örneği çalıştırmak için, <xref:System.Windows.Forms.BindingSource> kodu Adlandırılmış `BindingSource1` ve <xref:System.Windows.Forms.DataGridView> adlı `dataGridView1`bir forma yapıştırın. Olay işleyicisini yükle yönteminde form ve çağrı `InitializeSortedFilteredBindingSource` için olayıişleyin.<xref:System.Windows.Forms.Form.Load>  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.BindingSource.Sort%2A>
- <xref:System.Windows.Forms.BindingSource.Filter%2A>
- [Nasıl yapılır: Örnek veritabanlarını yükler](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/8b6y4c7s(v=vs.120))
- [BindingSource Bileşeni](bindingsource-component.md)
