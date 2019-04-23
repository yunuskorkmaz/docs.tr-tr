---
title: 'Nasıl yapılır: Tasarımcı Kullanarak bir Windows Forms Denetimini bir Türe Bağlama'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], binding to a type
- BindingSource component [Windows Forms], binding to a type
- types [Windows Forms], binding controls to
ms.assetid: 5ab984b5-c2d0-4638-a572-1c84013e8746
ms.openlocfilehash: b298efb0494994659673f9bf9893b667f7eb0f8c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59304220"
---
# <a name="how-to-bind-a-windows-forms-control-to-a-type-using-the-designer"></a>Nasıl yapılır: Tasarımcı Kullanarak bir Windows Forms Denetimini bir Türe Bağlama
Verilerle etkileşimde bulunmak denetimleri oluştururken, bazen bir nesne yerine bir tür bir denetimine bağlamak gerekir. Genelde bir denetimi tasarım zamanında ne zaman veri kullanılamıyor olabilir, ancak yine de bir türün ortak arabirim verileri görüntülemek için verilere bağlı denetimler istediğiniz bir türe bağlama gerekir. Aşağıdaki yordamlar yeni bir oluşturma işlemini göstermektedir <xref:System.Windows.Forms.BindingSource> olan bir türü için sınır ve sonra nasıl bir türün özelliklerine bağlanacağını <xref:System.Windows.Forms.TextBox.Text%2A> özelliği bir <xref:System.Windows.Forms.TextBox>.  
  
### <a name="to-bind-the-bindingsource-to-a-type"></a>BindingSource bir türe bağlama için  
  
1. Bir Windows Forms projesi oluşturun (**dosya** > **yeni** > **proje** > **Visual C#** veya **Visual Basic** > **Klasik Masaüstü** > **Windows Forms uygulamalarındaki**).  
  
2. İçinde **tasarım** görüntülemek için sürükleyin bir <xref:System.Windows.Forms.BindingSource> forma bileşen.  
  
3. İçinde **özellikleri** penceresinde için oka tıklayın <xref:System.Windows.Forms.BindingSource.DataSource%2A> özelliği.  
  
4. İçinde **DataSource UI türü düzenleyici**, tıklayın **proje veri kaynağı Ekle**.  
  
5. Üzerinde **bir veri kaynağı türü seçin** sayfasında **nesne** tıklatıp **sonraki**.  
  
6. Bağlanılacak türünü seçin:  
  
    -   Bağlamak istediğiniz türü geçerli projede veya türü içeren derlemeye bir başvuru olarak zaten eklendi, istediğiniz türünü bulmak için düğümleri genişletin ve ardından bu seçeneği belirleyin.  
  
         -veya-  
  
    -   Bağlamak istediğiniz türü olan başvuruları listesinde şu anda başka bir derlemede tıklarsanız **Başvuru Ekle**ve ardından **projeleri** sekmesi. ' A tıklayın ve istediğiniz iş nesnesi içeren projeyi seçin **Tamam**. Bu proje, derleme, listede görünür türü bulmak için düğümleri genişletebilirsiniz. Bu nedenle, istediğiniz ve ardından bu seçeneği belirleyin.  
  
        > [!NOTE]
        >  Framework ya da Microsoft derlemesi bir tür bağlamak istiyorsanız, Temizle **Gizle Microsoft veya sistem başlayan derlemeleri** onay kutusu.  
  
7. **İleri**'ye ve ardından **Son**'a tıklayın.  
  
### <a name="to-bind-the-control-to-the-bindingsource"></a>Denetimi için BindingSource bağlamak için  
  
1. Ekleme bir <xref:System.Windows.Forms.TextBox> form.  
  
2. İçinde **özellikleri** penceresini genişletin **(DataBindings)** düğümü.  
  
3. Yanındaki oka tıklayın <xref:System.Windows.Forms.TextBox.Text%2A> özelliği.  
  
4. İçinde **DataSource UI türü düzenleyici**, düğümünü genişletin <xref:System.Windows.Forms.BindingSource> daha önce eklenmiş ve istediğiniz bağlamak için ilişkili tür özelliğine seçin <xref:System.Windows.Forms.TextBox.Text%2A> özelliği <xref:System.Windows.Forms.TextBox>.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [BindingSource Bileşeni](bindingsource-component.md)
- [Nasıl yapılır: Bir Windows Forms denetimini bir türe bağlama](how-to-bind-a-windows-forms-control-to-a-type.md)
- [Visual Studio'da verilere denetimler bağlama](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)
