---
title: "Nasıl yapılır: Windows Formları için Denetimler Yazma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [Windows Forms], creating
- UserControl class [Windows Forms], Windows Forms
- custom controls [Windows Forms], creating
ms.assetid: 7570e982-545b-4c3a-a7c7-55581d313400
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f42ee49a4690c23a563740993e721207d5dedea0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-author-controls-for-windows-forms"></a>Nasıl yapılır: Windows Formları için Denetimler Yazma
Bir denetim kullanıcı ve program arasındaki grafik bağlantısını temsil eder. Bir denetim sağlayın veya verileri işlemek, kullanıcı girişi kabul, olaylara yanıt veya herhangi bir sayıda kullanıcı ve uygulama bağlanan diğer işlevleri gerçekleştirmek. Bir denetim bir bileşen aslında bir grafik arabirimle olduğundan, bir bileşen yapar, yanı sıra kullanıcı etkileşimi sağlayan herhangi bir işlev görebilir. Denetimleri belirli amaçlara hizmet için oluşturulan ve denetimleri yazma başka bir programlama bir görevdir. Aklınızda aşağıdaki adımları işlem yazma denetimine genel bakış temsil eder. Bağlantılar tek tek adımları ek bilgi sağlar.  
  
> [!NOTE]
>  Web Forms kullanmak için bkz: özel bir denetim yazmak istiyorsanız [özel ASP.NET sunucu denetimleri geliştirme](http://msdn.microsoft.com/library/fbe26c16-cff4-4089-b3dd-877411f0c0ef).  
>   
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-author-a-control"></a>Bir denetim yazmak için  
  
1.  Denetim gerçekleştirmek istediğiniz ya da bu kısım belirlemek, uygulamanızda yürütülür. Dikkat edilecek noktalar şunlardır:  
  
    -   Ne tür bir grafik arabirim gerekiyor?  
  
    -   Hangi belirli kullanıcı etkileşimleri bu denetim kullanacak mı?  
  
    -   Gereksinim duyduğunuz işlevselliği varolan tüm denetimleri tarafından sağlanır?  
  
    -   Çeşitli Windows Forms denetimleri bir araya getirerek gereksinim duyduğunuz işlevselliği alabilir miyim?  
  
2.  Denetim için nesne modeli gerekiyorsa, nasıl işlevselliği nesne modeli dağıtılmış ve işlevselliği denetim ve tüm alt nesnelerinin arasında bölmek belirleyin. Karmaşık bir denetim planlama ya da birkaç işlevler eklemek istediğiniz nesne modeli yararlı olabilir.  
  
3.  Tür belirleme denetimini (örneğin, kullanıcı denetimi, özel bir denetim, devralınan Windows Forms denetimi) gerekir. Ayrıntılar için bkz [denetim türü önerileri](../../../../docs/framework/winforms/controls/control-type-recommendations.md) ve [özel denetimler çeşit](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md).  
  
4.  Özellikleri, yöntemleri ve olayları denetimi ve alt nesnelerinin veya yan yapıları işlevleri hızlı ve uygun erişim düzeyleri (örneğin, ortak, korumalı vb.) atayın.  
  
5.  Denetimi için özel boyama gerekiyorsa, bunun için kodu ekleyin. Ayrıntılar için bkz [özel denetim boyama ve işleme](../../../../docs/framework/winforms/controls/custom-control-painting-and-rendering.md).  
  
6.  Denetim devraldığı varsa <xref:System.Windows.Forms.UserControl>, Denetim proje oluşturma ve çalışır durumda çalışma zamanı davranışını sınama **UserControl Test kapsayıcısı**. Daha fazla bilgi için bkz: [nasıl yapılır: bir UserControl denetiminin çalışma zamanı davranışını sınama](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).  
  
7.  Ayrıca, test ve bir Windows uygulaması gibi yeni bir proje oluşturma ve bir kapsayıcıya yerleştirme tarafından denetiminizi hata ayıklama. Bu işlemin bir parçası olarak gösterilen [izlenecek yol: Visual Basic ile bileşik denetim yazma](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-basic.md).  
  
8.  Her bir özellik ekler gibi özellikleri yeni işlevselliği kullanmak için test projenize ekleyin.  
  
9. Tasarım daraltmayı yineleyin.  
  
10. Paket ve denetiminizin dağıtın. Ayrıntılar için bkz [dağıtma uygulamaları, hizmetleri ve bileşenleri](https://msdn.microsoft.com/library/wtzawcsz).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İzlenecek yol: Visual Basic ile bileşik denetim yazma](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-basic.md)  
 [İzlenecek yol: Visual Basic ile beraber Windows Forms Denetimi'nden devralma](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic.md)  
 [Nasıl yapılır: UserControl sınıfından devralma](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-usercontrol-class.md)  
 [Nasıl yapılır: denetim sınıfından devralma](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-control-class.md)  
 [Nasıl yapılır: mevcut Windows Formları denetimlerinden devralma](../../../../docs/framework/winforms/controls/how-to-inherit-from-existing-windows-forms-controls.md)  
 [Nasıl yapılır: bir UserControl denetiminin çalışma zamanı davranışını sınama](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md)  
 [Özel denetim çeşitleri](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)
