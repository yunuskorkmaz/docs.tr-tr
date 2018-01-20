---
title: "Nasıl yapılır: Windows Formlarına Denetimler Kilitleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms controls, locking
- controls [Windows Forms], locking
ms.assetid: 94efe0d2-c14e-4d14-b903-63ea9b07e290
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7f5cd70e71a4a8bc48a3240055117dadc1086a50
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-lock-controls-to-windows-forms"></a>Nasıl yapılır: Windows Formlarına Denetimler Kilitleme
Windows uygulamanızın kullanıcı arabirimi (UI) tasarlarken, böylece istemeden taşıdığınızda veya diğer özellikleri ayarlanırken yeniden boyutlandırmak, doğru yer almasını sonra denetimleri kilitleyebilirsiniz.  
  
 Ayrıca, kilitleme ve tüm form üzerinde denetimleri birçok denetimleri ile formlar için yararlı olan aynı anda kilidini açma veya ayrı ayrı denetimler kilidini açabilir. Form üzerinde istediğiniz yere tüm denetimler yerleştirdiğiniz sonra bunları hatalı taşıma önlemek için tüm yerinde kilitleyin.  
  
> [!NOTE]
>  Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-lock-a-control"></a>Bir denetim kilitlemek için  
  
1.  İçinde **özellikleri** penceresinde tıklatın **kilitli** özelliği ve seçin `true`. (Ad çift özellik ayarı değiştirir.)  
  
     Alternatif olarak, denetimi sağ tıklatın ve seçin **kilit denetimleri**.  
  
    > [!NOTE]
    >  Denetimler kilitleme, bunları tasarım yüzeyine bir yeni boyutunu veya konumunu sürüklenmesini önleyerek engeller. Ancak, yine boyutunu veya denetimleri yoluyla konumunu değiştirebilirsiniz **özellikleri** penceresi veya kod.  
  
### <a name="to-lock-all-the-controls-on-a-form"></a>Formdaki tüm denetimler kilitlemek için  
  
1.  Gelen **biçimi** menüsünde seçin **kilit denetimleri**.  
  
    > [!NOTE]
    >  Bir form denetim olduğundan bu komut formun boyutu de kilitler.  
  
### <a name="to-unlock-all-locked-controls-on-a-form"></a>Tüm kilidini açmak için bir form üzerinde denetimleri kilitli  
  
1.  Gelen **biçimi** menüsünde seçin **kilit denetimleri**.  
  
     Tüm daha önce kilitli denetimleri form üzerinde sunulmuştur kilidi.  
  
### <a name="to-unlock-locked-controls-individually"></a>Kilitli denetimleri tek tek kilidini açmak için  
  
1.  İçinde **özellikleri** penceresinde tıklatın **kilitli** özelliği ve seçin `false`. (Ad çift özellik ayarı değiştirir.)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows Forms Denetimleri](../../../../docs/framework/winforms/controls/index.md)  
 [Windows Forms’da Denetimleri Düzenleme](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [Ayrı Windows Forms Denetimlerini Etiketleme ve Kısayollarını Sunma](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)  
 [Windows Forms'da Kullanılacak Denetimler](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 [İşleve Göre Windows Forms Denetimleri](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)
