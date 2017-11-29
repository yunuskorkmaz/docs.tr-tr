---
title: "Nasıl yapılır: Araç Kutusu Öğelerini Seç İletişim Kutusunda bir Denetimi Görüntüleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- global assembly cache [Windows Forms], Choose Toolbox Items dialog box
- AssemblyFoldersEx [Windows Forms], Choose Toolbox Items dialog box
- controls [Windows Forms], display in Choose Toolbox Items dialog box
- assembly folder registration [Windows Forms], Choose Toolbox Items dialog box
- Choose Toolbox Items dialog box [Windows Forms], display control
ms.assetid: 01ef6eba-d044-40f0-951d-78eff7ebd9a9
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f7bbb13e8a2b877d0f503e091b5bb8b1e7e89d00
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-display-a-control-in-the-choose-toolbox-items-dialog-box"></a>Nasıl yapılır: Araç Kutusu Öğelerini Seç İletişim Kutusunda bir Denetimi Görüntüleme
Geliştirme ve denetimleri dağıtmak gibi görünmesi bu denetimleri isteyebilirsiniz **araç kutusu öğelerini Seç** , sağ tıklattığınızda görüntülenen iletişim kutusunda, **araç** seçip  **Öğeleri seçin**. AssemblyFoldersEx kayıt yordamı kullanarak bu iletişim kutusunda görünmesi denetiminizi etkinleştirebilirsiniz.  
  
### <a name="to-display-your-control-in-the-choose-toolbox-items-dialog-box"></a>Araç kutusu öğelerini Seç iletişim kutusunda, Denetim görüntülemek için  
  
-   Denetim derleme genel derleme önbelleğine yükleyin. Daha fazla bilgi için bkz: [nasıl yapılır: bir derlemeyi genel derleme önbelleğine yükleme](../../../../docs/framework/app-domains/how-to-install-an-assembly-into-the-gac.md)  
  
     veya  
  
-   Denetim ve onun ilişkili tasarım zamanı derlemeleri AssemblyFoldersEx kayıt yordamı kullanarak kaydedin. AssemblyFoldersEx, üçüncü taraf satıcılar her destekledikleri framework sürümü için yollar depoladığınız bir kayıt defteri konumdur. Tasarım zamanı çözümleme başvuru derlemeleri bulmak için bu kayıt defteri konumunda bakabilirsiniz. Kayıt defteri komut dosyası araç kutusunda görünmesini istediğiniz denetimleri belirtebilirsiniz. Daha fazla bilgi için bkz: [bir özel denetim ve tasarım zamanı derlemeleri (Visual Studio 2013) dağıtma](http://msdn.microsoft.com/en-us/96158eb0-b691-4ae1-9e7b-3c65a1b798cb).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Araç kutusu öğelerini Seç iletişim kutusu (Visual Studio)](http://msdn.microsoft.com/en-us/bd07835f-18a8-433e-bccc-7141f65263bb)  
 [Özel bir denetim ve tasarım zamanı derlemeleri (Visual Studio 2013) dağıtma](http://msdn.microsoft.com/en-us/96158eb0-b691-4ae1-9e7b-3c65a1b798cb)  
 [Windows Forms denetimleri geliştirme tasarım zamanında](../../../../docs/framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)  
 [Nasıl yapılır: bir derlemeyi genel derleme önbelleğine yükleme](../../../../docs/framework/app-domains/how-to-install-an-assembly-into-the-gac.md)  
 [İzlenecek yol: Araç kutusunu özel bileşenlerle otomatik olarak doldurma](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
