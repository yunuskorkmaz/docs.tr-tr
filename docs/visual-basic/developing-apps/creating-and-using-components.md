---
description: 'Hakkında daha fazla bilgi edinin: Visual Basic bileşenleri oluşturma ve kullanma'
title: Bileşen Oluşturma ve Kullanma
ms.date: 07/20/2015
helpviewer_keywords:
- components [Visual Basic]
ms.assetid: ee6a4156-73f7-4e9b-8e01-c74c4798b65c
ms.openlocfilehash: f59b4774556d95dcbc1befb16409d68a51c50535
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99666595"
---
# <a name="creating-and-using-components-in-visual-basic"></a>Visual Basic'te Bileşenler Oluşturma ve Kullanma

*Bileşen* , <xref:System.ComponentModel.IComponent?displayProperty=nameWithType> arabirimini uygulayan veya uygulayan bir sınıftan doğrudan veya dolaylı olarak türetilen bir sınıftır <xref:System.ComponentModel.IComponent> . .NET bileşeni, yeniden kullanılabilen, diğer nesnelerle etkileşime girebilen bir nesnedir ve dış kaynaklar ve tasarım zamanı desteği üzerinde denetim sağlar.  
  
 Bileşenlerin önemli bir özelliği, bir bileşen olan bir sınıfın Visual Studio tümleşik geliştirme ortamında kullanılabileceği anlamına gelir. Araç kutusuna bir bileşen eklenebilir, sürüklenip bir forma bırakılabilir ve tasarım yüzeyinde değiştirilebilir. Bileşenler için temel tasarım zamanı desteği .NET içinde yerleşiktir. Bir bileşen geliştiricisi, temel tasarım zamanı işlevlerinin avantajlarından yararlanmak için ek bir iş yapmak zorunda değildir.  
  
 Bir *Denetim* , bir bileşene benzer, her ikisi de göstergeler olur. Ancak, bir denetim bir kullanıcı arabirimi sağlar, ancak bir bileşen desteklemez. Bir denetim, taban denetim sınıflarından birinden türetilmelidir: <xref:System.Windows.Forms.Control> veya <xref:System.Web.UI.Control> .  
  
## <a name="when-to-create-a-component"></a>Bileşen ne zaman oluşturulur  

 Sınıfınız bir tasarım yüzeyinde (Windows Forms veya Web Forms Tasarımcısı gibi) kullanılacaksa ancak kullanıcı arabirimine sahip değilse, bir bileşen olmalıdır ve <xref:System.ComponentModel.IComponent> doğrudan veya dolaylı olarak uygulayan bir sınıftan türetilmiş olmalıdır <xref:System.ComponentModel.IComponent> .  
  
 <xref:System.ComponentModel.Component>Ve <xref:System.ComponentModel.MarshalByValueComponent> sınıfları, arabiriminin temel uygulamalarıdır <xref:System.ComponentModel.IComponent> . Bu sınıflar arasındaki temel fark, <xref:System.ComponentModel.Component> sınıfın başvuruya göre sıralanmasına karşın <xref:System.ComponentModel.IComponent> değere göre sıralanmalarıdır. Aşağıdaki liste, ımplemenonun için kapsamlı yönergeler sağlar.  
  
- Bileşeninizin başvuruya göre sıralanması gerekiyorsa, öğesinden türetebilirsiniz <xref:System.ComponentModel.Component> .  
  
- Bileşeninizin değere göre sıralanması gerekiyorsa, öğesinden türetebilirsiniz <xref:System.ComponentModel.MarshalByValueComponent> .  
  
- Tek devralma nedeniyle bileşeniniz temel uygulamalardan birinden türetilemiyor <xref:System.ComponentModel.IComponent> .  
  
## <a name="component-classes"></a>Bileşen Sınıfları  

 <xref:System.ComponentModel>Ad alanı, bileşenlerin ve denetimlerin çalışma zamanı ve tasarım zamanı davranışını uygulamak için kullanılan sınıfları sağlar. Bu ad alanı, öznitelik ve tür dönüştürücülerini uygulamaya yönelik temel sınıfları ve arabirimleri, veri kaynaklarına bağlamayı ve Lisans bileşenlerini içerir.  
  
 Çekirdek bileşen sınıfları şunlardır:  
  
- <xref:System.ComponentModel.Component>. Arabirim için temel uygulama <xref:System.ComponentModel.IComponent> . Bu sınıf, uygulamalar arasında nesne paylaşımına izin vermez.  
  
- <xref:System.ComponentModel.MarshalByValueComponent>. Arabirim için temel uygulama <xref:System.ComponentModel.IComponent> .  
  
- <xref:System.ComponentModel.Container>. Arabirim için temel uygulama <xref:System.ComponentModel.IContainer> . Bu sınıf sıfır veya daha fazla bileşeni kapsüller.  
  
 Bileşen lisanslama için kullanılan sınıflardan bazıları şunlardır:  
  
- <xref:System.ComponentModel.License>. Tüm lisanslar için soyut temel sınıf. Bir bileşenin belirli bir örneğine bir lisans verilir.  
  
- <xref:System.ComponentModel.LicenseManager>. Bir bileşene lisans eklemek ve ' a yönetmek için özellikler ve yöntemler sağlar <xref:System.ComponentModel.LicenseProvider> .  
  
- <xref:System.ComponentModel.LicenseProvider>. Bir lisans sağlayıcısını uygulamaya yönelik soyut temel sınıf.  
  
- <xref:System.ComponentModel.LicenseProviderAttribute>. <xref:System.ComponentModel.LicenseProvider>Bir sınıfla kullanılacak sınıfı belirtir.  
  
 Yaygın olarak bileşenleri tanımlamak ve sürdürmek için kullanılan sınıflar.  
  
- <xref:System.ComponentModel.TypeDescriptor>. Bir bileşenin öznitelikleri, özellikleri ve olayları gibi özellikleri hakkında bilgi sağlar.  
  
- <xref:System.ComponentModel.EventDescriptor>. Bir olay hakkında bilgi sağlar.  
  
- <xref:System.ComponentModel.PropertyDescriptor>. Bir özellik hakkında bilgi sağlar.  
  
## <a name="related-sections"></a>İlgili Bölümler  

 [Denetim ve Bileşen Yazmada Sorun Giderme](/dotnet/desktop/winforms/controls/troubleshooting-control-and-component-authoring)  
 Yaygın sorunların nasıl düzeltileceğini açıklar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Windows Forms Design-Time desteğe erişme](/dotnet/desktop/winforms/controls/developing-windows-forms-controls-at-design-time)
