---
title: "Nasıl yapılır: Belirlenemeyen Derinliğe Sahip Veriyi TreeView'a Bağlama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: TreeView control [WPF], binding to data of indeterminate depth
ms.assetid: daddcd74-1b0f-4ffd-baeb-ec934c5e0f53
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b16cae3a91eae73a4480484d89bb075862256b25
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-bind-a-treeview-to-data-that-has-an-indeterminable-depth"></a>Nasıl yapılır: Belirlenemeyen Derinliğe Sahip Veriyi TreeView'a Bağlama
Bağlamak istediğiniz zamanlar olabilir bir <xref:System.Windows.Controls.TreeView> Derinliği bilinmeyen bir veri kaynağına.  Veriler çalışanların diğer çalışanlarla doğrudan rapor sahip olduğu doğal olarak burada klasörleri klasörler içerebilir, bir dosya sistemi veya bir şirketin kuruluş yapısı gibi özyinelemeli olduğunda bu durum oluşabilir.  
  
 Veri kaynağı hiyerarşik nesne modeli yüklü olmalıdır. Örneğin, bir `Employee` sınıfı, bir çalışanın doğrudan rapor çalışan nesneler koleksiyonu içerebilir. Verileri hiyerarşik olmayan bir şekilde gösteriliyorsa, verileri hiyerarşik bir gösterimini oluşturmanız gerekir.  
  
 Ayarladığınızda <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A?displayProperty=nameWithType> özelliği ve <xref:System.Windows.Controls.ItemsControl> oluşturur bir <xref:System.Windows.Controls.ItemsControl> her bir alt öğe, sonra alt için <xref:System.Windows.Controls.ItemsControl> aynı kullanan <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> üst olarak. Örneğin, ayarlarsanız <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> verilere bağlı özellikte <xref:System.Windows.Controls.TreeView>, her <xref:System.Windows.Controls.TreeViewItem> diğer bir deyişle oluşturulan kullanır <xref:System.Windows.DataTemplate> için atandı <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> özelliği <xref:System.Windows.Controls.TreeView>.  
  
 <xref:System.Windows.HierarchicalDataTemplate> Belirtmenize olanak tanıyan <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> için bir <xref:System.Windows.Controls.TreeViewItem>, veya tüm <xref:System.Windows.Controls.HeaderedItemsControl>, veri şablonu üzerinde. Ayarladığınızda <xref:System.Windows.HierarchicalDataTemplate.ItemsSource%2A?displayProperty=nameWithType> değer özelliği, ne zaman kullanılan <xref:System.Windows.HierarchicalDataTemplate> uygulanır. Kullanarak bir <xref:System.Windows.HierarchicalDataTemplate>, yinelemeli olarak ayarlayabilirsiniz <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> her <xref:System.Windows.Controls.TreeViewItem> içinde <xref:System.Windows.Controls.TreeView>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte nasıl bağlanacağını gösterir bir <xref:System.Windows.Controls.TreeView> hiyerarşik veri ve kullanmak için bir <xref:System.Windows.HierarchicalDataTemplate> belirtmek için <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> her <xref:System.Windows.Controls.TreeViewItem>.  <xref:System.Windows.Controls.TreeView> Bir şirkette çalışanları temsil eden XML verilerine bağlar.  Her `Employee` öğesi diğer içerebilir `Employee` kimin kime rapor belirtmek için öğeleri. Verileri özyinelemeli olduğundan <xref:System.Windows.HierarchicalDataTemplate> her düzeye uygulanabilir.  
  
 [!code-xaml[TreeViewWithUnknownDepth#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewWithUnknownDepth/CS/Window1.xaml#1)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri bağlama genel bakış](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Veri şablonu özeti](../../../../docs/framework/wpf/data/data-templating-overview.md)
