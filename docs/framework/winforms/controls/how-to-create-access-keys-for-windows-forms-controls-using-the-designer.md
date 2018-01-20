---
title: "Nasıl yapılır: Tasarımcı Kullanarak Windows Formları Denetimleri için Erişim Tuşları Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [Windows Forms], access keys
- Button control [Windows Forms], access keys
- dialog box controls [Windows Forms], mnemonics
- access keys [Windows Forms], creating for controls
- mnemonics [Windows Forms], adding to dialog box controls
- ampersand character in shortcut key
- Windows Forms controls, access keys
- examples [Windows Forms], controls
- Text property [Windows Forms], specifying access keys for controls
- keyboard shortcuts [Windows Forms], creating for controls
- access keys [Windows Forms], Windows Forms
- ALT key
ms.assetid: 4c374c4c-4ca9-4a68-ac96-9dc3ab0f518a
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ed3bf2aa1e6081ca018f1b4dec98e6304a1aa95c
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-create-access-keys-for-windows-forms-controls-using-the-designer"></a>Nasıl yapılır: Tasarımcı Kullanarak Windows Formları Denetimleri için Erişim Tuşları Oluşturma
Bir *erişim tuşu* altı çizili bir karakter menü, menü öğesi ya da bir düğmesi gibi denetimin etiket metnini,'dir. "Bir düğme önceden tanımlanmış erişim anahtarı ile birlikte ALT tuşuna basarak tıklayın" kullanıcının sağlar. Örneğin, bir düğme bir form yazdırma için bir yordam çalıştırıyorsa ve bu nedenle, `Text` "P" neden harfi "altı çizili P" düğmesi metni çalışma zamanında harf önce "ve işareti ekleme Yazdır," (&) özelliğini ayarlayın. Kullanıcı ilişkili düğme ALT + S tuşlarına basarak komutu çalıştırabilirsiniz. Odağı alamayan bir denetim için erişim tuşu sahip olamaz.  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-create-an-access-key-for-a-control"></a>Bir denetim için erişim anahtarı oluşturmak için  
  
1.  İçinde **özellikleri** penceresindeki ayarlayın `Text` özellik erişim tuşu olacaktır harf önce ve işareti içeren bir dize için (&). Örneğin, harf "P" erişim tuşu olarak ayarlamak için şunu yazın **& Yazdırma** kılavuz içine.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.Button>  
 [Nasıl yapılır: Windows Forms Düğme Tıklamalarına Yanıt Verme](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)  
 [Nasıl yapılır: Windows Forms Denetimi Tarafından Görüntülenen Metni Ayarlama](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md)  
 [Ayrı Windows Forms Denetimlerini Etiketleme ve Kısayollarını Sunma](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
