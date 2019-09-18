---
title: Derlemeler ve Genel Derleme Önbelleği ile Çalışma
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- global assembly cache, benefits
- ACLs [.NET Framework]
- GAC (global assembly cache), benefits
- access control lists [.NET Framework]
ms.assetid: 8a18e5c2-d41d-49ef-abcb-7c27e2469433
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0331e0ad30743d5f0bba125e8e61e636e1c2a5be
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053022"
---
# <a name="working-with-assemblies-and-the-global-assembly-cache"></a>Derlemeler ve Genel Derleme Önbelleği ile Çalışma

Eğer bir derlemeyi birden çok uygulama arasında paylaşmak istiyorsanız, bu derlemeyi genel bütünleştirilmiş kod önbelleğine yükleyebilirsiniz. Ortak dil çalışma zamanının yüklü olduğu tüm bilgisayarlar, makine düzeyindeki bu kod önbelleğine sahiptir. Genel bütünleştirilmiş kod önbelleği, bilgisayardaki çeşitli uygulamalar tarafından paylaşılmak üzere özel olarak belirlenmiş derlemeleri depolar. Bir derlemenin genel bütünleştirilmiş kod önbelleğine yüklenebilmesi için tanımlayıcı ada sahip olması gerekir.  
  
> [!NOTE]
> Genel bütünleştirilmiş kod önbelleğine yerleştirilen derlemeler aynı derleme adı ve dosya adına sahip olmalıdır (dosya adı uzantısı dahil değil). Örneğin, myAssembly derleme adına sahip bir derlemenin, myAssembly.exe ya da myAssembly.dll dosya adı olmalıdır.  
  
Derlemeleri, yalnızca gerektiğinde genel bütünleştirilmiş kod önbelleğine yükleyerek paylaşmalısınız. Derlemeyi paylaşmanız kesinlikle gerekli olmadığı sürece, genel bir kılavuz olarak, derleme bağımlılıklarını özel tutun ve derlemeleri uygulama dizinine yerleştirin. Ek olarak, derlemeleri COM ile birlikte çalışmaya veya yönetilmeyen koda erişilebilir yapmak için genel bütünleştirilmiş kod önbelleğine yüklemeniz gerekli değildir.  
  
Bir derlemeyi genel bütünleştirilmiş kod önbelleğine yüklemek istemeniz için birkaç neden vardır:  
  
- Paylaşılan konum.  
  
     Uygulamalar tarafından kullanılması gereken derlemeler genel bütünleştirilmiş kod önbelleğine konulabilir. Örneğin, eğer tüm uygulamaların genel bütünleştirilmiş kod önbelleğinde bulunan bir derlemeyi kullanması gerekiyorsa bir sürüm ilkesi, başvuruları derlemeye yeniden yönlendiren Machine.config dosyasına eklenebilir.  
  
- Dosya güvenliği.  
  
     Yöneticiler, yazma ve yürütme erişimini denetlemek için systemroot dizinini genellikle bir Erişim Denetim Listesi (ACL) kullanarak korur. Genel bütünleştirilmiş kod önbelleği systemroot dizininde yüklü olduğu için, bu dizinin ACL'sini devralır. Yalnızca yönetici ayrıcalıklarına sahip kullanıcıların, dosyaları genel derleme önbelleğinden silmesine izin verilmesi önerilir.  
  
- Yan yana sürüm oluşturma.  
  
     Genel bütünleştirilmiş kod önbelleğinde derlemelerin aynı ada ancak farklı sürüm bilgisine sahip olan birden çok kopyası tutulabilir.  
  
- Ek arama konumu.  
  
     Ortak dil çalışma zamanı, bir yapılandırma dosyasındaki kod temeli bilgisini algılamadan veya kullanmadan önce, derleme isteğiyle eşleşen bir derleme için genel bütünleştirilmiş kod önbelleğini kontrol eder.  
  
 Bir derlemeyi genel bütünleştirilmiş kod önbelleğine açıkça yüklemek istemeyeceğiniz senaryolar olduğuna dikkat edin. Eğer bir uygulamayı oluşturan derlemelerden birini genel bütünleştirilmiş kod önbelleğine yerleştirirseniz, uygulama dizinini kopyalamak için XCOPY'i kullanarak uygulamayı artık çoğaltamaz veya yükleyemezsiniz. Bu durumda, derlemeyi de genel bütünleştirilmiş kod önbelleğine taşımanız gerekir.  
  
## <a name="in-this-section"></a>Bu Bölümde  
[Nasıl yapılır: Bir derlemeyi genel bütünleştirilmiş kod önbelleğine yükler](install-assembly-into-gac.md)  
Bir derlemeyi genel bütünleştirilmiş kod belleğine yükleme yöntemlerini açıklar.  
  
[Nasıl yapılır: Genel derleme önbelleğinin Içeriğini görüntüleme](how-to-view-the-contents-of-the-gac.md)  
Küresel derleme önbelleğinin içeriğini görüntülemek için [Gacutil. exe ' nin (genel bütünleştirilmiş kod önbelleği aracı)](../tools/gacutil-exe-gac-tool.md) nasıl kullanılacağını açıklar.  
  
[Nasıl yapılır: Bir derlemeyi genel bütünleştirilmiş kod önbelleğinden kaldırma](how-to-remove-an-assembly-from-the-gac.md)  
Bir derlemeyi genel bütünleştirilmiş kod önbelleğinden kaldırmak için [Gacutil. exe ' nin (genel bütünleştirilmiş kod önbelleği aracı)](../tools/gacutil-exe-gac-tool.md) nasıl kullanılacağını açıklar.  
  
[Genel Derleme Önbelleği ile Hizmet Verilen Bileşenleri Kullanma](use-serviced-components-with-the-gac.md)  
Hizmet verilen bileşenlerin (yönetilen COM+ bileşenleri) neden genel bütünleştirilmiş kod önbelleğine yerleştirilmesi gerektiğini açıklar.  
  
## <a name="related-sections"></a>İlgili Bölümler  

[Bütünleştirilmiş Kodlar Oluşturma](../../standard/assembly/create.md)  
Derleme oluşturmaya genel bir bakış sağlar.  
  
[Genel Derleme Önbelleği](gac.md)  
Genel bütünleştirilmiş kod önbelleğini açıklar.  
  
[Nasıl yapılır: Derleme Içeriğini görüntüle](../../standard/assembly/view-contents.md)  
Bir derlemede Microsoft ara dili (MSIL) bilgilerini görüntülemek için [ıldadsm. exe ' nin (IL Disassembler)](../tools/ildasm-exe-il-disassembler.md) nasıl kullanılacağını açıklar.  
  
[Çalışma Zamanının Bütünleştirilmiş Kodların Konumunu Bulması](../deployment/how-the-runtime-locates-assemblies.md)  
Ortak dil çalışma zamanının uygulamanızı oluşturan derlemeleri nasıl konumlandırdığını ve yüklediğini açıklar.  
  
[Bütünleştirilmiş Kodlarla Programlama](../../standard/assembly/program.md)  
Yönetilen uygulamaların yapı taşları olan derlemeleri açıklar.
