---
title: "Nasıl yapılır: UserControl Sınıfından Devralma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- UserControl class [Windows Forms], inheriting from
- user controls [Windows Forms], creating
- composite controls [Windows Forms], creating
ms.assetid: 67713625-e2e4-4f6a-bce7-0855ee5043d9
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5eec04e6122f32321c34efe030bfca943baed5bf
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-inherit-from-the-usercontrol-class"></a>Nasıl yapılır: UserControl Sınıfından Devralma
Özel kod ile bir veya daha fazla Windows Forms denetimleri işlevselliğini birleştirmek için oluşturabileceğiniz bir *kullanıcı denetimi*. Kullanıcı denetimleri hızlı denetimi geliştirme birleştirmek, işlevsellik ve özel özellikler ve yöntemler yönlülük standart Windows Forms denetimi. Bir kullanıcı denetimi oluşturma başladığınızda,, standart Windows Forms denetimleri yerleştirebileceğiniz görünür tasarımcı ile birlikte sunulur. Bu denetimler tüm devralınmış işlevselliklerini yanı sıra görünümünü ve standart denetimler (Görünüm) davranışını korur. Bu denetimleri içinde kullanıcı denetimini yerleşiktir sonra ancak bunlar artık kod üzerinden kullanılabilir. Kullanıcı denetimi kendi boyama yapar ve ayrıca tüm denetimleriyle ilişkili temel işlevleri yürütür.  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-create-a-user-control"></a>Bir kullanıcı denetimi oluşturmak için  
  
1.  Yeni bir **Windows Denetim Kitaplığı** projesi.  
  
     Yeni bir proje boş kullanıcı denetimi ile oluşturulur.  
  
2.  Sürükleme denetimlerden **Windows Forms** sekmesinde **araç** , tasarımcıya.  
  
3.  Bu denetimler konumlandırılmış ve son kullanıcı denetiminde görünmesini istediğiniz şekilde tasarlanmıştır. Bağlı denetimler erişmek geliştiricilere izin vermek istiyorsanız, ortak olarak bildirme veya bağlı denetimi özellikleri, seçmeli olarak kullanıma gerekir. Ayrıntılar için bkz [nasıl yapılır: destekçi denetimleri özellikleri kullanıma](../../../../docs/framework/winforms/controls/how-to-expose-properties-of-constituent-controls.md).  
  
4.  Herhangi bir özel yöntemler veya denetiminizi dahil özellikler uygular.  
  
5.  Projeyi derlemek ve denetiminizin çalıştırmak için F5 tuşuna basın **UserControl Test kapsayıcısı**. Daha fazla bilgi için bkz: [nasıl yapılır: bir UserControl denetiminin çalışma zamanı davranışını sınama](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Özel Denetim Çeşitleri](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)  
 [Nasıl yapılır: Denetim Sınıfından Devralma](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-control-class.md)  
 [Nasıl yapılır: Mevcut Windows Forms Denetimlerinden Devralma](../../../../docs/framework/winforms/controls/how-to-inherit-from-existing-windows-forms-controls.md)  
 [Nasıl yapılır: Windows Forms için Denetimler Yazma](../../../../docs/framework/winforms/controls/how-to-author-controls-for-windows-forms.md)  
 [Devralınmış olay işleyicileri Visual Basic sorunlarını giderme](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)  
 [Nasıl yapılır: Bir UserControl Denetiminin Çalışma Zamanı Davranışını Sınama](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md)
