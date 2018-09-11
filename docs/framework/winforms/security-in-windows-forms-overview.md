---
title: Windows Forms'ta Güvenliğe Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- code access security [Windows Forms], Windows Forms
- permissions [Windows Forms], Windows Forms
- Windows Forms, security
- security [Windows Forms], about security
- access control [Windows Forms], Windows Forms
ms.assetid: 4810dc9f-ea23-4ce1-8ea1-657f0ff1d820
ms.openlocfilehash: 54fc56e5e7d6ee5cd0e7bc55bd22c7d4127eb4d3
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/11/2018
ms.locfileid: "44353794"
---
# <a name="security-in-windows-forms-overview"></a>Windows Forms'ta Güvenliğe Genel Bakış
Yayınlanmadan önce [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], çalışan tüm kod bir kullanıcı bilgisayar aynı haklarını veya bilgisayarın kullanıcısı olan kaynaklara erişim izinleri olan kullanıcının. Örneğin, kullanıcının dosya sistemine erişim izni, kod dosya sistemine erişebilir izin; Kullanıcı bir veritabanına erişmek için izin verilen, kod veritabanına erişmeye izin. Bu hak ve izinler kullanıcı açıkça yerel bilgisayarda yüklü olan yürütülebilir dosyaları, kod için kabul edilebilir olsa da, bunlar Internet veya yerel Intranet gelen kötü amaçlı kodlar için kabul edilebilir olmayabilir. Bu kod, kullanıcının izni olmadan bilgisayar kaynaklarına erişebilmesi olmamalıdır.  
  
 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Adlı kod erişimi güvenliği izinleri veya kullanıcının sahip olduğu hakları koduna sahip hakları ayırt olanak tanıyan bir altyapı sunar. Varsayılan olarak, Internet ve Intranet gelen kod yalnızca kısmi güven bilinen içinde çalıştırabilirsiniz. Kısmi güven konuları kısıtlamaları bir dizi uygulamaya: diğer özelliklerin yanı sıra, bir uygulamanın yerel sabit disk erişimi sınırlıdır ve yönetilmeyen kod çalıştıramazsınız. [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Kod erişmek için bu kod kimliğine izin kaynakları denetler: nereden geldiğini içerip içermediğine, bir [Strong-Named derlemeleri](../../../docs/framework/app-domains/strong-named-assemblies.md), bir sertifika ve benzeri ile imzalı olup olmadığını.  
  
 [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] Windows Forms uygulamaları dağıtmak için kullandığınız, teknoloji, yardımcı olur, kısmi güven, tam güven veya kısmi güven yükseltilmiş izinlerle çalışan uygulamalar geliştirmek kolaylaştırır. [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] İzin yükseltilmesi ve güvenilir uygulama dağıtımı gibi özellikler sağlar, böylece uygulama tam güven veya yükseltilmiş izinler yerel kullanıcı sorumlu bir şekilde talep edebilir.  
  
## <a name="understanding-security-in-the-net-framework"></a>.NET Framework Güvenliği anlama  
 Kod erişimi güvenliği, kodun diğer yönleri ve kod kaynaklandığı bağlı olarak değişen düzeylerde güvenilir olması için kod sağlar. Ortak dil çalışma zamanı kullanan güvenlik ilkesi belirlemek için kanıt hakkında daha fazla bilgi için bkz. [kanıt](https://msdn.microsoft.com/library/64ceb7c8-a0b4-46c4-97dc-6c22da0539da). Bilgisayar sistemlerini kötü amaçlı koddan korunmasına yardımcı olur ve kasıtlı olarak veya yanlışlıkla güvenlikten ödün güvenilen kod korunmasına yardımcı olur. Yalnızca uygulamanız için gereken izinleri belirtebildiğinizden kod erişimi güvenliği, uygulamanız, hangi eylemleri üzerinde daha fazla denetim sağlar. Bile bu kod bir tek kod-erişim-security yapma izni denetimi kod erişimi güvenliği, ortak dil çalışma zamanını hedefleyen tüm yönetilen kodun etkiler. Güvenlik hakkında daha fazla bilgi için [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], bkz: [temel güvenlik kavramları](../../../docs/standard/security/key-security-concepts.md) ve [kod erişimi güvenliği Temelleri](../../../docs/framework/misc/code-access-security-basics.md).  
  
 Kullanıcı bir Windows Forms yürütülebilir dosyayı doğrudan bir Web sunucusu veya dosya paylaşımı dışına çalıştırırsanız, derecede güven, uygulamaya verilen kod bulunduğu ve kullanmaya nasıl bağlıdır. Bir uygulama çalıştırdığında, otomatik olarak değerlendirilir ve ortak dil çalışma zamanını şuradan adlandırılmış bir izin kümesini alır. Varsayılan olarak, yerel bilgisayardan kod tam güven izni verilir ayarlayın, bir yerel ağ koddan yerel Intranet izin kümesi verilir ve Internet'ten kod Internet izni verilir.  
  
> [!NOTE]
>  İçinde [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] sürüm 1.0 Service Pack 1 ve Service Pack 2, Internet bölgesi kod grubunun hiçbir şey yapmayın aldığı izin kümesi. Diğer tüm sürümlerinde [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], Internet bölgesi kod grubunda ayarlanmış Internet izinleri alır.  
>   
>  Her, bu izin kümeleri varsayılan izinler listelenir [varsayılan güvenlik ilkesini](https://msdn.microsoft.com/library/2c086873-0894-4f4d-8f7e-47427c1a3b55) konu. Uygulamanın aldığı izinlerine bağlı olarak düzgün çalışıyor ya da bir güvenlik özel durumu oluşturur.  
>   
>  Çok sayıda Windows Forms uygulamaları kullanarak dağıtılacak [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)]. Oluşturmak için kullanılan araçları bir [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] dağıtımınız ne daha önce bahsedilen daha farklı güvenlik Varsayılanları. Daha fazla bilgi için aşağıdaki tartışmalara bakın.  
  
 Güvenlik İlkesi değiştirilebildiğinden, uygulamanız için gerçek izinler varsayılan değerlerden farklı olabilir; başka bir deyişle, bir bilgisayarda, ancak başka bir uygulama izni olabilir.  
  
## <a name="developing-a-more-secure-windows-forms-application"></a>Daha güvenli bir Windows Forms uygulaması geliştirme  
 Güvenlik, uygulama geliştirme tüm adımları önemlidir. Başlangıç gözden geçirerek ve aşağıdaki [güvenli kodlama kılavuzları](../../../docs/standard/security/secure-coding-guidelines.md).  
  
 Ardından, uygulama tam güven çalışıp gerekir veya kısmi güvende mi çalıştırılması gereken karar verin. Uygulamanızın tam güvende çalıştırma yerel bilgisayardaki kaynaklara erişmeye kolaylaştırır, ancak etmez tasarım ve güvenli kodlama yönergeleri kesinlikle göre uygulamanızı geliştirmek, uygulamanız ve onun kullanıcıları için yüksek güvenlik riskleri sunar. konu. Uygulamanızı kısmi güvende çalışan daha güvenli uygulama geliştirmeyi daha kolay hale getirir ve çok riskini azaltır, ancak daha fazla belirli özellikleri uygulamak nasıl planlama gerektirir.  
  
 Kısmi güven (diğer bir deyişle, ya da Internet veya yerel Intranet izin kümeleri) tercih ederseniz bu ortamda mono'da uygulamanızın nasıl istediğinize karar verin. Windows Forms, yarı güvenilir bir ortamda özellikleri uygulamak için daha güvenli, alternatif yollar sağlar. Veri erişimi gibi uygulamanızın belirli bölümlerini tasarlanmış ve kısmi güven hem de tam güven ortamlar için farklı bir şekilde yazılmış. Uygulama ayarları gibi bazı Windows Forms özellikleri, kısmi güven çalışacak şekilde tasarlanmıştır. Daha fazla bilgi için [uygulama ayarlarına genel bakış](../../../docs/framework/winforms/advanced/application-settings-overview.md).  
  
 Kısmi güven verir, ancak tam güvende çalıştırmak istiyor musunuz daha fazla izin uygulamanız gerekiyorsa, yalnızca gereksinim duyduğunuz ek izinler sunduğundan çalışırken kısmi güvende çalıştırabilirsiniz. Örneğin, kısmi güvende çalıştırmak istediğiniz, ancak kullanıcının dosya sistemindeki bir dizin, uygulama yalnızca okuma erişimi vermeniz gerekir, isteyebileceğiniz <xref:System.Security.Permissions.FileIOPermission> yalnızca bu dizin için. Bu yaklaşım, doğru kullanıldığında, uygulamanızın artırılmış işlevselliğini sağlamak ve kullanıcılarınıza güvenlik riskleri en aza indirmek.  
  
 Kısmi güvende çalışan bir uygulama geliştirdiğinizde, uygulamanızın çalıştırmalısınız hangi izinlerin izlemek ve hangi izinlerin uygulamanızı isteğe bağlı olarak kullanabilirsiniz. Tüm izinleri olduğunda, bildirim temelli bir uygulama düzeyinde izin isteği olmanız gerekir. İzinleri bildiren isteyen [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] hangi izinleri hakkında uygulamanızın ihtiyaç duyduğu ve hangi izinlerin özellikle değil istediğiniz zaman çalıştırın. İzinler isteyen hakkında daha fazla bilgi için bkz: [izinleri isteyen](https://msdn.microsoft.com/library/0447c49d-8cba-45e4-862c-ff0b59bebdc2).  
  
 İsteğe bağlı izinler istediğinde, uygulamanızı kendisine verilmemiş izinleri gerektiren bir eylem gerçekleştirdiğinde oluşturulacak güvenlik özel durumlarını işlemelidir. Uygun olan işleme <xref:System.Security.SecurityException> uygulamanızın çalışmaya devam edebilir sağlayacaktır. Uygulamanızın özel durum, kullanıcı için bir özelliği devre haline olup olmadığını belirlemek için kullanabilirsiniz. Örneğin, bir uygulamanın devre dışı bırakabilirsiniz **Kaydet** gerekli dosya iznin verilmediği, menü seçeneği.  
  
 Bazı durumlarda, onaylanan tüm uygun izinleri varsa bilmek zordur. Yüzeysel olarak zararsız görünen bir yöntem çağrısının, örneğin, yürütme sırasında belirli bir noktada dosya sistemi erişebilir. Uygulamanızı gerekli tüm izinlere sahip dağıtılmaz, masaüstünüzde hata ayıklamak, ancak dağıtıldığında başarısız olduğunda bunu ince test. Her iki [!INCLUDE[dnprdnlong](../../../includes/dnprdnlong-md.md)] SDK ve [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] bir uygulama için gerekli olan izinleri hesaplamak için araçları içerir: MT.exe komut satırı aracı ve Visual Studio'nun hesaplama izinleri özelliği sırasıyla.  
  
 Aşağıdaki konular, ek Windows Forms güvenlik özellikleri açıklanmaktadır.  
  
|Konu|Açıklama|  
|-----------|-----------------|  
|-   [Daha güvenli dosya ve Windows Forms veri erişimi](../../../docs/framework/winforms/more-secure-file-and-data-access-in-windows-forms.md)|Dosyaları ve verileri kısmi güven ortamında nasıl açıklar.|  
|-   [Windows Forms'ta daha güvenli yazdırma](../../../docs/framework/winforms/more-secure-printing-in-windows-forms.md)|Kısmi güven ortamında yazdırma özelliklerine erişmek nasıl açıklar.|  
|-   [Windows Forms'ta ek güvenlik konuları](../../../docs/framework/winforms/additional-security-considerations-in-windows-forms.md)|Pano'yu kullanıyor ve yönetilmeyen kodu bir kısmi güven ortamında aramaların gerçekleştirme penceresi işleme açıklar.|  
  
-  
  
### <a name="deploying-an-application-with-the-appropriate-permissions"></a>Uygun izinlere sahip bir uygulama dağıtma  
 Bir istemci bilgisayar için bir Windows Forms uygulaması dağıtmanın en yaygın ile yöntemdir [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)], çalıştırılacak tüm bileşenlerin açıklayan bir dağıtım teknolojisi uygulamanızın ihtiyaç duyduğu. [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] bildirimleri, uygulamanızı oluşturan dosyalar ve derlemeleri tanımlamak için kullandığı XML dosyaları adlı ve ayrıca uygulama izinleri gerektirir.  
  
 [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] İstemci bilgisayarda yükseltilmiş izinler isteyen iki teknoloji var. Her iki teknolojinin Authenticode sertifikalarının kullanımı hakkında kullanır. Sertifikalar, uygulamanın güvenilir bir kaynaktan geldi kullanıcılarınıza bazı güvencesi sağlamaya yardımcı.  
  
 Aşağıdaki tabloda bu teknolojiler açıklanmaktadır.  
  
|Yükseltilmiş izin teknolojisi|Açıklama|  
|------------------------------------|-----------------|  
|İzin yükseltilmesi|Uygulamanızı bir güvenlik iletişim kutusu ilk çalıştığında kullanıcıya sorar. **İzin yükseltilmesi** iletişim kutusu bildirir kullanıcı uygulama yayımlanan kim yapabilmesi kullanıcı ek güven verme konusunda bilinçli bir karar|  
|Güvenilir uygulama dağıtımı|Bir istemci bilgisayarda bir yayımcının Authenticode sertifikası tek seferlik bir yüklemesini gerçekleştirme bir Sistem Yöneticisi içerir. Bu noktadan itibaren tüm uygulamaları otomatik olarak imzalanan sertifika ile kabul olarak güvenilir ve tam güven ek sorgu yapmadan yerel bilgisayarda çalıştırabilirsiniz.|  
  
 Seçtiğiniz teknolojileri dağıtım ortamınıza bağlıdır. Daha fazla bilgi için [ClickOnce dağıtım stratejisini seçme](/visualstudio/deployment/choosing-a-clickonce-deployment-strategy).  
  
 Varsayılan olarak, [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] ya da Visual Studio kullanarak dağıtılmış uygulamalar veya [!INCLUDE[dnprdnlong](../../../includes/dnprdnlong-md.md)] SDK Araçları (Mage.exe ve MageUI.exe) tam güveni olan bir istemci bilgisayarda çalışması için yapılandırılır. Uygulamanızı kısmi güveni kullanmaya veya bazı ek izinler kullanarak dağıtıyorsanız bu varsayılanı değiştirmek gerekecektir. Visual Studio ile bunu yapabilirsiniz veya [!INCLUDE[dnprdnlong](../../../includes/dnprdnlong-md.md)] dağıtımınız yapılandırdığınızda MageUI.exe SDK aracıdır. İzlenecek yol MageUI.exe kullanma hakkında daha fazla bilgi için bkz: bir ClickOnce uygulamasını komut satırından dağıtma.  Ayrıca bkz: [nasıl yapılır: ClickOnce uygulaması için özel izinler ayarlayın](https://msdn.microsoft.com/library/hafybdaa\(v=vs.110\)) veya [nasıl yapılır: ClickOnce uygulaması için özel izinler ayarlayın](https://msdn.microsoft.com/library/hafybdaa\(v=vs.120\)).  
  
 Güvenlik yönleri hakkında daha fazla bilgi için [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] ve izin yükseltme bakın, [ClickOnce uygulamalarının güvenliğini sağlama](/visualstudio/deployment/securing-clickonce-applications). Güvenilir uygulama dağıtımı hakkında daha fazla bilgi için bkz: [Trusted Application Deployment Overview](/visualstudio/deployment/trusted-application-deployment-overview).  
  
### <a name="testing-the-application"></a>Uygulamayı Test Etme  
 Visual Studio kullanarak, Windows Forms uygulaması dağıttıysanız, kısmi güven veya geliştirme ortamından ayarlanan sınırlı izin kümesinde hata ayıklamayı etkinleştirebilirsiniz.  Ayrıca bkz: [nasıl yapılır: sınırlı izinler ile ClickOnce uygulamasında hata ayıklama](https://msdn.microsoft.com/library/593zkfdf\(v=vs.110\)) veya [nasıl yapılır: sınırlı izinler ile ClickOnce uygulamasında hata ayıklama](https://msdn.microsoft.com/library/593zkfdf\(v=vs.120\)).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows Forms Güvenliği](../../../docs/framework/winforms/windows-forms-security.md)  
 [Kod erişimi güvenliği temelleri](../../../docs/framework/misc/code-access-security-basics.md)  
 [ClickOnce Güvenliği ve Dağıtımı](/visualstudio/deployment/clickonce-security-and-deployment)  
 [Güvenilir Uygulama Dağıtımına Genel Bakış](/visualstudio/deployment/trusted-application-deployment-overview)  
 [Mage.exe (Bildirim Oluşturma ve Düzenleme Aracı)](../../../docs/framework/tools/mage-exe-manifest-generation-and-editing-tool.md)  
 [MageUI.exe (Bildirim Oluşturma ve Düzenleme Aracı, Grafik İstemci)](../../../docs/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client.md)
