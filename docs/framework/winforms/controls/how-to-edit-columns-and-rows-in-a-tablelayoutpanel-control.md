---
title: "Nasıl yapılır: Bir TableLayoutPanel Denetimindeki Satırları ve Sütunları Düzenleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- net.ComponentModel.StyleCollectionEditor
helpviewer_keywords:
- columns [Windows Forms], editing
- TableLayoutPanel control [Windows Forms], editing
- rows [Windows Forms], editing
ms.assetid: c367ed43-40dc-49eb-9e0f-ba70e83dfec0
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: bf54a02a409bead598a4e98315d5709e55677f3b
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-edit-columns-and-rows-in-a-tablelayoutpanel-control"></a>Nasıl yapılır: Bir TableLayoutPanel Denetimindeki Satırları ve Sütunları Düzenleme
Koleksiyon Düzenleyicisi kullanımını <xref:System.Windows.Forms.TableLayoutPanel> adlı Denetim **sütun ve satır stilleri** iletişim kutusu, satırları ve sütunları, denetimlerinizin düzenlemek için.  
  
> [!NOTE]
>  Birden çok satır veya sütun yayılan bir denetim istiyorsanız ayarlayın `RowSpan` ve `ColumnSpan` denetimi özellikleri. Daha fazla bilgi için bkz: [izlenecek yol: Windows Forms kullanarak bir TableLayoutPanel düzenleme denetimleri](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).  
>   
>  Hücre içindeki bir denetimi hizalama istiyorsanız veya içinde bir hücre uzatmak için bir denetim istiyorsanız, denetimin kullanmak <xref:System.Windows.Forms.Control.Anchor%2A> özelliği. Daha fazla bilgi için bkz: [izlenecek yol: Windows Forms kullanarak bir TableLayoutPanel düzenleme denetimleri](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md).  
>   
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-edit-rows-and-columns"></a>Satırları ve sütunları düzenlemek için  
  
1.  Sürükleme bir <xref:System.Windows.Forms.TableLayoutPanel> gelen denetim **araç** formunuza.  
  
2.  Tıklatın <xref:System.Windows.Forms.TableLayoutPanel> denetimin akıllı etiket karakteri (![akıllı etiket karakteri](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) seçip **Düzenle satırları ve sütunları** açmak için  **Sütun ve satır stilleri** iletişim kutusu. Ayrıca sağ tıklayarak <xref:System.Windows.Forms.TableLayoutPanel> denetlemek ve seçin **Düzenle satırları ve sütunları** kısayol menüsünden.  
  
3.  Sütun eklemek veya kaldırmak için seçin **sütunları** gelen **üye türü** aşağı açılan liste kutusu.  
  
4.  Satır eklediğinizde veya kaldırdığınızda için seçin **satırları** gelen **üye türü** aşağı açılan liste kutusu.  
  
5.  Tıklatın **Ekle** sonuna satır veya sütun eklemek için düğmeyi **üye** listesi.  
  
6.  Tıklatın **Ekle** bir satır veya sütun seçili öğenin önce listesine eklemek için düğmesi.  
  
7.  Bir satır veya sütun ekliyorsanız seçin **boyutu türü** yeni satır veya sütun. Daha fazla bilgi için bkz. <xref:System.Windows.Forms.SizeType>.  
  
8.  Bir satır veya sütun kaldırmak için tıklatın **kaldırmak** şu anda seçilen öğeyi silmek için düğmesini **üye** listesi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.SizeType>  
 [TableLayoutPanel Denetimi](../../../../docs/framework/winforms/controls/tablelayoutpanel-control-windows-forms.md)
