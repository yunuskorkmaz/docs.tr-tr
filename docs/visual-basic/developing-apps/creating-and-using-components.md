---
title: Bileşen Oluşturma ve Kullanma
ms.date: 07/20/2015
helpviewer_keywords:
- components [Visual Basic]
ms.assetid: ee6a4156-73f7-4e9b-8e01-c74c4798b65c
ms.openlocfilehash: 2fefdff9dc27915066e3d92efd8439adffed9fc5
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74330292"
---
# <a name="creating-and-using-components-in-visual-basic"></a>Visual Basic'te Bileşenler Oluşturma ve Kullanma

*Bileşen* <xref:System.ComponentModel.IComponent?displayProperty=nameWithType> arabirimini uygulayan veya <xref:System.ComponentModel.IComponent>uygulayan bir sınıftan doğrudan veya dolaylı olarak türetilen bir sınıftır. .NET Framework bileşen yeniden kullanılabilir olan, diğer nesnelerle etkileşime girebilen ve dış kaynaklar ve tasarım zamanı desteği üzerinde denetim sağlayan bir nesnedir.  
  
 Bileşenlerin önemli bir özelliği, bir bileşen olan bir sınıfın Visual Studio tümleşik geliştirme ortamında kullanılabileceği anlamına gelir. Araç kutusuna bir bileşen eklenebilir, sürüklenip bir forma bırakılabilir ve tasarım yüzeyinde değiştirilebilir. Bileşenler için temel tasarım zamanı desteğinin .NET Framework yerleşik olduğuna dikkat edin; bir bileşen geliştiricisi, temel tasarım zamanı işlevlerinin avantajlarından yararlanmak için ek bir iş yapmak zorunda değildir.  
  
 Bir *Denetim* , bir bileşene benzer, her ikisi de göstergeler olur. Ancak, bir denetim bir kullanıcı arabirimi sağlar, ancak bir bileşen desteklemez. Bir denetim, temel denetim sınıflarından birini türetmelidir: <xref:System.Windows.Forms.Control> veya <xref:System.Web.UI.Control>.  
  
## <a name="when-to-create-a-component"></a>Bileşen ne zaman oluşturulur  

 Sınıfınız bir tasarım yüzeyinde (Windows Forms veya Web Forms Tasarımcısı gibi) kullanılacaksa ancak kullanıcı arabirimine sahip değilse, bir bileşen olmalı ve <xref:System.ComponentModel.IComponent>uygulamalıdır ya da doğrudan veya dolaylı olarak <xref:System.ComponentModel.IComponent>uygulayan bir sınıftan türetirsiniz.  
  
 <xref:System.ComponentModel.Component> ve <xref:System.ComponentModel.MarshalByValueComponent> sınıfları <xref:System.ComponentModel.IComponent> arabiriminin temel uygulamalarıdır. Bu sınıflar arasındaki temel fark, <xref:System.ComponentModel.Component> sınıfının başvuruya göre sıralanmasına karşın <xref:System.ComponentModel.IComponent> değere göre sıralanır. Aşağıdaki liste, ımplemenonun için kapsamlı yönergeler sağlar.  
  
- Bileşeninizin başvuruya göre sıralanması gerekiyorsa <xref:System.ComponentModel.Component>türetirsiniz.  
  
- Bileşeninizin değere göre sıralanması gerekiyorsa <xref:System.ComponentModel.MarshalByValueComponent>türetirsiniz.  
  
- Tek devralma nedeniyle bileşeniniz temel uygulamalardan birinden türetilemiyor <xref:System.ComponentModel.IComponent>uygulayın.  
  
## <a name="component-classes"></a>Bileşen Sınıfları  

 <xref:System.ComponentModel> ad alanı, bileşenlerin ve denetimlerin çalışma zamanı ve tasarım zamanı davranışını uygulamak için kullanılan sınıfları sağlar. Bu ad alanı, öznitelik ve tür dönüştürücülerini uygulamaya yönelik temel sınıfları ve arabirimleri, veri kaynaklarına bağlamayı ve Lisans bileşenlerini içerir.  
  
 Çekirdek bileşen sınıfları şunlardır:  
  
- <xref:System.ComponentModel.Component>. <xref:System.ComponentModel.IComponent> arabirimi için temel uygulama. Bu sınıf, uygulamalar arasında nesne paylaşımına izin vermez.  
  
- <xref:System.ComponentModel.MarshalByValueComponent>. <xref:System.ComponentModel.IComponent> arabirimi için temel uygulama.  
  
- <xref:System.ComponentModel.Container>. <xref:System.ComponentModel.IContainer> arabirimi için temel uygulama. Bu sınıf sıfır veya daha fazla bileşeni kapsüller.  
  
 Bileşen lisanslama için kullanılan sınıflardan bazıları şunlardır:  
  
- <xref:System.ComponentModel.License>. Tüm lisanslar için soyut temel sınıf. Bir bileşenin belirli bir örneğine bir lisans verilir.  
  
- <xref:System.ComponentModel.LicenseManager>. Bir bileşene lisans eklemek ve bir <xref:System.ComponentModel.LicenseProvider>yönetmek için özellikler ve yöntemler sağlar.  
  
- <xref:System.ComponentModel.LicenseProvider>. Bir lisans sağlayıcısını uygulamaya yönelik soyut temel sınıf.  
  
- <xref:System.ComponentModel.LicenseProviderAttribute>. Bir sınıfla kullanılacak <xref:System.ComponentModel.LicenseProvider> sınıfını belirtir.  
  
 Yaygın olarak bileşenleri tanımlamak ve sürdürmek için kullanılan sınıflar.  
  
- <xref:System.ComponentModel.TypeDescriptor>. Bir bileşenin öznitelikleri, özellikleri ve olayları gibi özellikleri hakkında bilgi sağlar.  
  
- <xref:System.ComponentModel.EventDescriptor>. Bir olay hakkında bilgi sağlar.  
  
- <xref:System.ComponentModel.PropertyDescriptor>. Bir özellik hakkında bilgi sağlar.  
  
## <a name="related-sections"></a>İlgili Bölümler  

 [Denetim ve Bileşen Yazmada Sorun Giderme](../../framework/winforms/controls/troubleshooting-control-and-component-authoring.md)  
 Yaygın sorunların nasıl düzeltileceğini açıklar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Windows Forms 'de tasarım zamanı desteğine erişme](../../framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)
