---
title: "Nasıl yapılır: Tasarımcı Kullanarak bir Windows Formları Denetimini bir Türe Bağlama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [Windows Forms], binding to a type
- BindingSource component [Windows Forms], binding to a type
- types [Windows Forms], binding controls to
ms.assetid: 5ab984b5-c2d0-4638-a572-1c84013e8746
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ee932e7cb4a3333ac56242e281ec64d3016746f9
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-bind-a-windows-forms-control-to-a-type-using-the-designer"></a>Nasıl yapılır: Tasarımcı Kullanarak bir Windows Formları Denetimini bir Türe Bağlama
Verilerle etkileşimli denetimleri oluştururken, bazen bir nesne yerine bir tür bir denetimi bağlamak gerekir. Genellikle bir denetim tasarım zamanında ne zaman veri kullanılamıyor olabilir, ancak hala bir türün ortak arabirimi verileri görüntülemek için veri bağlama denetimleri istediğiniz bir türe bağlama gerekir. Aşağıdaki yordamlarda yeni bir oluşturma gösterilmektedir <xref:System.Windows.Forms.BindingSource> diğer bir deyişle bir tür için sınır ve ardından tür özelliklerinden biri nasıl bağlanacağı <xref:System.Windows.Forms.TextBox.Text%2A> özelliği bir <xref:System.Windows.Forms.TextBox>.  
  
### <a name="to-bind-the-bindingsource-to-a-type"></a>BindingSource bir türe bağlama  
  
1.  Bir Windows Forms projesi oluşturun.  
  
     Daha fazla bilgi için bkz: [nasıl yapılır: bir Windows uygulaması projesi oluşturduğunuzda](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa).  
  
2.  İçinde **tasarım** görüntülemek için sürükleyin bir <xref:System.Windows.Forms.BindingSource> forma bileşen.  
  
3.  İçinde **özellikleri** penceresinde oka tıklayın <xref:System.Windows.Forms.BindingSource.DataSource%2A> özelliği.  
  
4.  İçinde **DataSource UI türü düzenleyici**, tıklatın **proje veri kaynağı Ekle**.  
  
5.  Üzerinde **bir veri kaynağı türü seç** sayfasında, **nesne** tıklatıp **sonraki**.  
  
6.  Bağlamak üzere türünü seçin:  
  
    -   Bağlamak istediğiniz türü geçerli proje veya türünü içeren bütünleştirilmiş kodun bir başvuru olarak zaten eklendi istediğiniz türünü bulmak için düğümleri genişletin ve ardından seçin.  
  
         veya  
  
    -   Bağlamak istediğiniz türü olan başvuruları listesinde şu anda başka bir derlemede tıklatırsanız **Başvuru Ekle**ve ardından **projeleri** sekmesi. İstediğiniz iş nesnesini içeren projeyi seçin **Tamam**. Bu proje derlemeler, listede görünür türü bulmak için düğümlerini genişletin şekilde, istediğiniz ve ardından seçin.  
  
        > [!NOTE]
        >  Bir türe framework ya da Microsoft derleme bağlamak istiyorsanız, temizleyin **Gizle Microsoft veya sistem başlayan derlemeleri** onay kutusu.  
  
7.  **İleri**'ye ve ardından **Son**'a tıklayın.  
  
### <a name="to-bind-the-control-to-the-bindingsource"></a>BindingSource denetimi bağlamak için  
  
1.  Ekleme bir <xref:System.Windows.Forms.TextBox> form.  
  
2.  İçinde **özellikleri** penceresinde genişletin **(veri bağlamaları)** düğümü.  
  
3.  Yanındaki oka tıklayın <xref:System.Windows.Forms.TextBox.Text%2A> özelliği.  
  
4.  İçinde **DataSource UI türü düzenleyici**, düğümünü genişletin <xref:System.Windows.Forms.BindingSource> daha önce eklediğiniz ve bağlamak istediğiniz ilişkili tür özelliğine seçin <xref:System.Windows.Forms.TextBox.Text%2A> özelliği <xref:System.Windows.Forms.TextBox>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [BindingSource Bileşeni](../../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [Nasıl yapılır: Windows Forms Denetimini Bir Türe Bağlama](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)  
 [Visual Studio'da verilere denetimler bağlama](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)
