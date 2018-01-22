---
title: "Nasıl yapılır Windows Forms ListView Denetimindeki Öğeleri Gruplama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView control [Windows Forms], grouping items
- lists [Windows Forms], grouping items
- grouping
- list views [Windows Forms], grouping items
- groups
- groups [Windows Forms], in Windows Forms controls
ms.assetid: 610416a1-8da4-436c-af19-5f19e654769b
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0f9596d5a344b2e14ea73120a4d2412917eba365
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-group-items-in-a-windows-forms-listview-control"></a>Nasıl yapılır Windows Forms ListView Denetimindeki Öğeleri Gruplama
Gruplama özelliğiyle <xref:System.Windows.Forms.ListView> denetimi gruplarında ilgili öğeleri kümesi görüntüleyebilirsiniz. Bu gruplar ekranda grup başlıklarını içeren yatay grup üstbilgileri tarafından ayrılır. Kullanabileceğiniz <xref:System.Windows.Forms.ListView> öğeleri alfabetik olarak tarihe ya da diğer bir mantıksal gruplandırma göre gruplandırarak büyük listelerini daha kolay gezinme olmak için grupları. Aşağıdaki resimde gruplandırılmış bazı öğeler gösterilir.  
  
 ![ListView grupları](../../../../docs/framework/winforms/controls/media/listviewgroups.gif "ListViewGroups")  
ListView gruplandırılmış öğeleri  
  
 Gruplandırma etkinleştirmek için önce bir veya daha fazla grupları Tasarımcısı'nda veya programlı olarak oluşturmanız gerekir. Bir grup tanımlandıktan sonra atayabilirsiniz <xref:System.Windows.Forms.ListView> öğeleri gruplarına. Ayrıca öğeleri bir gruptan başka bir program aracılığıyla taşıyabilirsiniz.  
  
> [!NOTE]
>  <xref:System.Windows.Forms.ListView>gruplar yalnızca [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] uygulamanızı çağırdığında <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> yöntemi. Önceki işletim sistemlerinde gruplarına ilgili herhangi bir kod hiçbir etkisi olmaz ve grupları görüntülenmez. Daha fazla bilgi için bkz. <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>.  
  
### <a name="to-add-groups"></a>Grup eklemek için  
  
1.  Kullanım <xref:System.Windows.Forms.ListViewGroupCollection.Add%2A> yöntemi <xref:System.Windows.Forms.ListView.Groups%2A> koleksiyonu.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#21)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#21)]  
  
### <a name="to-remove-groups"></a>Gruplarını kaldırmak için  
  
1.  Kullanım <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> veya <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> yöntemi <xref:System.Windows.Forms.ListView.Groups%2A> koleksiyonu.  
  
     <xref:System.Windows.Forms.ListViewGroupCollection.RemoveAt%2A> Yöntemi, tek bir grup kaldırır; <xref:System.Windows.Forms.ListViewGroupCollection.Clear%2A> yöntemi tüm grupları listeden kaldırır.  
  
    > [!NOTE]
    >  Grup kaldırma o grup dahilindeki öğeleri kaldırmaz.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#22](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#22)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#22](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#22)]  
  
### <a name="to-assign-items-to-groups-or-move-items-between-groups"></a>Öğeleri gruplarına atayın veya öğeleri grupları arasında taşımak için  
  
1.  Ayarlama <xref:System.Windows.Forms.ListViewItem.Group%2A?displayProperty=nameWithType> tek tek öğelerin özelliği.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#23)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#23)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.ListView>  
 <xref:System.Windows.Forms.ListView.Groups%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.ListViewGroup>  
 [ListView Denetimi](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)  
 [ListView Denetimine Genel Bakış](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)  
 [Windows XP özellikleri ve Windows Forms denetimleri](http://msdn.microsoft.com/library/bc7fab94-fce9-4bf1-a8ad-a5837c91c3c0)  
 [Nasıl yapılır: Windows Forms ListView Denetimi ile Öğe Ekleme ve Kaldırma](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
