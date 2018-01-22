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
ms.workload: dotnet
ms.openlocfilehash: 3964551ba2eec0980541e95a7db20ef057a1dd61
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-display-a-control-in-the-choose-toolbox-items-dialog-box"></a>Nasıl yapılır: Araç Kutusu Öğelerini Seç İletişim Kutusunda bir Denetimi Görüntüleme
Geliştirme ve denetimleri dağıtmak gibi görünmesi bu denetimleri isteyebilirsiniz **araç kutusu öğelerini Seç** , sağ tıklattığınızda görüntülenen iletişim kutusunda, **araç** seçip  **Öğeleri seçin**. AssemblyFoldersEx kayıt yordamı kullanarak bu iletişim kutusunda görünmesi denetiminizi etkinleştirebilirsiniz.  
  
### <a name="to-display-your-control-in-the-choose-toolbox-items-dialog-box"></a>Araç kutusu öğelerini Seç iletişim kutusunda, Denetim görüntülemek için  
  
-   Denetim derleme genel derleme önbelleğine yükleyin. Daha fazla bilgi için bkz: [nasıl yapılır: bir derlemeyi genel derleme önbelleğine yükleme](../../../../docs/framework/app-domains/how-to-install-an-assembly-into-the-gac.md)  
  
     veya  
  
-   Denetim ve onun ilişkili tasarım zamanı derlemeleri AssemblyFoldersEx kayıt yordamı kullanarak kaydedin. AssemblyFoldersEx, üçüncü taraf satıcılar her destekledikleri framework sürümü için yollar depoladığınız bir kayıt defteri konumdur. Tasarım zamanı çözümleme başvuru derlemeleri bulmak için bu kayıt defteri konumunda bakabilirsiniz. Kayıt defteri komut dosyası araç kutusunda görünmesini istediğiniz denetimleri belirtebilirsiniz. Daha fazla bilgi için bkz: [bir özel denetim ve tasarım zamanı derlemeleri (Visual Studio 2013) dağıtma](http://msdn.microsoft.com/library/96158eb0-b691-4ae1-9e7b-3c65a1b798cb).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Araç kutusu öğelerini Seç iletişim kutusu (Visual Studio)](http://msdn.microsoft.com/library/bd07835f-18a8-433e-bccc-7141f65263bb)  
 [Özel bir denetim ve tasarım zamanı derlemeleri (Visual Studio 2013) dağıtma](http://msdn.microsoft.com/library/96158eb0-b691-4ae1-9e7b-3c65a1b798cb)  
 [Tasarım Zamanında Windows Forms Denetimleri Geliştirme](../../../../docs/framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)  
 [Nasıl yapılır: Bir Bütünleştirilmiş Kodu Genel Derleme Önbelleğine Yükleme](../../../../docs/framework/app-domains/how-to-install-an-assembly-into-the-gac.md)  
 [İzlenecek yol: Araç Kutusunu Otomatik Olarak Özel Bileşenlerle Doldurma](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
