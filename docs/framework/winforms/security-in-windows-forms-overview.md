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
ms.openlocfilehash: ef90daa9700a60e3d88f75439bf8511b67a71dda
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33541417"
---
# <a name="security-in-windows-forms-overview"></a>Windows Forms'ta Güvenliğe Genel Bakış
' İn yayımlanmasından önce [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], çalışan tüm kod bir kullanıcı bilgisayar aynı hakları veya bilgisayarın kullanıcısı olan kaynaklara erişim izinleri olan kullanıcının. Örneğin, kullanıcının dosya sistemine erişim izni varsa, kodu dosya sistemi erişmesine izin; Kullanıcı bir veritabanına erişmek için izin verilen, o veritabanına erişmek için kod izin. Bu hak ve izinler kullanıcı açıkça yerel bilgisayarda yüklü yürütülebilir dosyalarında kod için kabul edilebilir olmakla birlikte, bunlar Internet veya yerel Intranet gelen zararlı kod için kabul edilebilir olmayabilir. Bu kodu izniniz olmadan kullanıcının bilgisayar kaynaklarına erişebildiğini olmamalıdır.  
  
 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] İzinleri veya kod kullanıcının sahip olduğu haklara sahip hakları ayırt olanak sağlayan bir kod erişim güvenliği adlı bir altyapı sunar. Varsayılan olarak, Internet ve intranet'ten gelen kod yalnızca kısmi güven olarak bilinen de çalıştırabilirsiniz. Kısmi güven konuları kısıtlamaları bir dizi uygulamaya: başka şeylerin uygulama yerel sabit diske erişmesini sınırlıdır ve yönetilmeyen kod çalıştırılamıyor. [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Kod erişmek için bu kodu kimliğine göre izin kaynakları denetler: nereden geldiğini onu olup, bir [Strong-Named derlemeleri](../../../docs/framework/app-domains/strong-named-assemblies.md), bir sertifika vb. ile imzalanıp imzalanmadığı.  
  
 [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] Windows Forms uygulamaları dağıtmak için kullanın, teknoloji yardımcı olur, kısmi güven, tam güven veya kısmi güven yükseltilmiş izinler ile çalışan uygulamalar geliştirmek kolaylaştırır. [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] Böylece, uygulama tam güven veya yükseltilmiş izinler yerel kullanıcıdan sorumlu bir şekilde isteyebilir izin yükseltme ve güvenilir uygulama dağıtımı gibi özellikler sağlar.  
  
## <a name="understanding-security-in-the-net-framework"></a>.NET Framework Güvenliği anlama  
 Kod erişim güvenliği değişen derecelerde, diğer yönlerini kodun kimlik ve kod kaynaklandığı bağlı olarak güvenilir olması için kod sağlar. Ortak dil çalışma zamanı güvenlik ilkesini belirlemek için kullanır kanıt hakkında daha fazla bilgi için bkz: [kanıt](http://msdn.microsoft.com/library/64ceb7c8-a0b4-46c4-97dc-6c22da0539da). Bilgisayar sistemleri kötü amaçlı koddan korunmasına yardımcı olur ve kasıtlı olarak veya kazayla güvenliği tehlikeye güvenilen kod korumaya yardımcı olur. Yalnızca uygulamanız için gereken izinleri belirtebildiğinizden kod erişim güvenliği, ayrıca, uygulamanızın neler yapabileceğinizi üzerinde daha fazla denetim sağlar. Bu kod değil tek kod-access-güvenlik yapma izni denetimi gerçekleştirir olsa bile kod erişim güvenliği ortak dil çalışma zamanı hedefleyen tüm yönetilen kod etkiler. Güvenlik konusunda daha fazla bilgi için [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], bkz: [temel güvenlik kavramları](../../../docs/standard/security/key-security-concepts.md) ve [kod erişim güvenliği Temelleri](../../../docs/framework/misc/code-access-security-basics.md).  
  
 Kullanıcı bir Windows Forms yürütülebilir dosya doğrudan bir Web sunucusuna veya bir dosya paylaşımı dışına çalıştırırsanız, uygulamanız için verilen güven düzeyini kodu bulunduğu ve nasıl başlatılacağını bağlıdır. Bir uygulama çalıştırıldığında otomatik olarak değerlendirilir ve ortak dil çalışma zamanı ' adlandırılmış izin kümesini alır. Varsayılan olarak, yerel bilgisayardan kodu tam güven izni verilir ayarlayın, bir yerel ağ koddan yerel Intranet izni verilir ve Internet'ten kod Internet izni verilir.  
  
> [!NOTE]
>  İçinde [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] sürüm 1.0 Service Pack 1 ve Service Pack 2, Internet bölgesi kod grubu alan hiçbir şey yapmayın izin kümesi. Diğer tüm sürümlerinde [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], Internet izinler kümesi Internet bölge kodu grubunu alır.  
>   
>  Her bu izin kümeleri varsayılan izinler listelenir [varsayılan güvenlik ilkesi](http://msdn.microsoft.com/library/2c086873-0894-4f4d-8f7e-47427c1a3b55) konu. Uygulama alan izinlerine bağlı olarak düzgün çalışıyor ya da bir güvenlik özel durumu oluşturur.  
>   
>  Çok sayıda Windows Forms uygulamaları kullanarak dağıtılacak [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)]. Oluşturmak için kullanılan araçlar bir [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] dağıtımınız ne yukarıda açıklanan daha farklı güvenlik Varsayılanları. Daha fazla bilgi için aşağıdaki tartışma bakın.  
  
 Güvenlik İlkesi değiştirilebildiğinden uygulamanızı gerçek izinler varsayılan değerlerinden farklı olabilir; Bu, uygulamanızın tek bir bilgisayarda, ancak başka izninizin olduğundan emin anlamına gelir.  
  
## <a name="developing-a-more-secure-windows-forms-application"></a>Daha güvenli bir Windows Forms uygulaması geliştirme  
 Güvenlik, uygulama geliştirme tüm adımda önemlidir. Gözden geçirme ve aşağıdaki başlangıç [güvenli kodlama yönergeleri](../../../docs/standard/security/secure-coding-guidelines.md).  
  
 Ardından, uygulamanızın tam güvende olup çalıştırmanız gerekir ya da kısmi güvende olup çalışmalı karar verin. Tam güvende uygulamanızı çalıştıran yerel bilgisayardaki kaynaklara erişimi kolay hale getirir, ancak, değil tasarlayıp uygulamanızı kesinlikle güvenli kodlama yönergelerine göre uygulamanızı ve yüksek güvenlik riskleri, kullanıcılara gösterir konu. Kısmi güvende uygulamanızı çalıştıran daha güvenli bir uygulama geliştirmek kolaylaştırır ve çok riskini azaltır, ancak daha fazla belirli özellikleri uygulamak nasıl planlama gerektirir.  
  
 Kısmi güven (diğer bir deyişle, ya da Internet veya yerel Intranet izin kümeleri) seçerseniz, uygulamanız bu ortamda davranmasına istediğiniz nasıl karar verin. Windows Forms zaman yarı güvenilir bir ortamda özellikleri uygulamak için alternatif, daha güvenli yolu sağlar. Uygulamanızın veri erişim gibi bazı bölümleri tasarlanmış ve kısmi güven ve tam güven ortamları için farklı bir şekilde yazılabilir. Uygulama ayarları gibi bazı Windows Forms özellikleri, kısmi güvende çalışmak üzere tasarlanmıştır. Daha fazla bilgi için bkz: [uygulama ayarlarına genel bakış](../../../docs/framework/winforms/advanced/application-settings-overview.md).  
  
 Uygulamanızın kısmi güven verir, ancak tam güvende çalıştırmak istiyor musunuz daha fazla izin gerekirse, yalnızca gereksinim duyduğunuz ek izinler sunduğundan sırasında kısmi güvende çalıştırabilirsiniz. Kısmi güvende çalıştırmak istediğiniz, ancak bir dizine kullanıcının dosya sistemindeki Uygulama salt okunur erişim vermeniz gerekir, örneğin, isteyebilir <xref:System.Security.Permissions.FileIOPermission> yalnızca bu dizin için. Bu yaklaşım, doğru şekilde kullanıldığında, uygulama artırılmış işlevsellik sağlar ve kullanıcılarınız için güvenlik riskleri en aza.  
  
 Kısmi güvende çalışacak bir uygulama geliştirirken, uygulamanızın çalıştırmalısınız hangi izinlerin izlemek ve hangi izinlerin, uygulamanızın isteğe bağlı olarak kullanabilirsiniz. Tüm izinleri bilindiğinde ise uygulama düzeyinde izin bildirim temelli bir isteği olmalısınız. İzinleri bildirir isteyen [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] uygulamanızın hangi izinleri hakkında gerektiğini ve hangi izinlerin özellikle değil istediğiniz zaman çalıştırın. İstekte bulunan izinleri hakkında daha fazla bilgi için bkz: [izinleri isteyen](http://msdn.microsoft.com/library/0447c49d-8cba-45e4-862c-ff0b59bebdc2).  
  
 İsteğe bağlı izinleri istediğinde, uygulamanızı yazma izni, izinleri gerektiren bir eylem gerçekleştirirse, oluşturulacak güvenlik özel durumları işleme gerekir. İşleme uygun <xref:System.Security.SecurityException> uygulamanız çalışmaya devam edebilir güvence altına alır. Uygulamanızı özel durum, kullanıcı için bir özellik devre hale olup olmadığını belirlemek için kullanabilirsiniz. Örneğin, bir uygulama devre dışı bırakabilirsiniz **kaydetmek** gerekli dosya izni olmayan verilirse menü seçeneği.  
  
 Bazı durumlarda, uygulanan tüm uygun izinleri varsa bilmek zordur. Yüzey üzerinde zararsız görünen bir yöntem çağrısı, örneğin, belirli bir noktada dosya sistemi yürütmesi sırasında erişebilir. Uygulamanız gerekli izinlere sahip değil dağıtırsanız, masaüstünüzde hata ayıklama, ancak dağıtıldığında başarısız olduğunda iyi test. Her iki [!INCLUDE[dnprdnlong](../../../includes/dnprdnlong-md.md)] SDK ve [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] uygulama gerekli olan izinleri hesaplamak için Araçlar içerir: MT.exe komut satırı aracı ve Visual Studio hesaplamak izinleri özelliğini sırasıyla.  
  
 Aşağıdaki konularda ek Windows Forms güvenlik özellikleri açıklanmaktadır.  
  
|Konu|Açıklama|  
|-----------|-----------------|  
|-   [Daha güvenli dosya ve Windows Forms veri erişimi](../../../docs/framework/winforms/more-secure-file-and-data-access-in-windows-forms.md)|Dosyaları ve verileri bir kısmi güven ortamında erişmek açıklar.|  
|-   [Windows Forms'ta daha güvenli yazdırma](../../../docs/framework/winforms/more-secure-printing-in-windows-forms.md)|Kısmi güven ortamında yazdırma özelliklerine erişmek açıklar.|  
|-   [Windows Forms'ta ek güvenlik konuları](../../../docs/framework/winforms/additional-security-considerations-in-windows-forms.md)|Pano kullanma ve bir kısmi güven ortamında yönetilmeyen kod aramalarına gerçekleştirme penceresi işleme açıklar.|  
  
-  
  
### <a name="deploying-an-application-with-the-appropriate-permissions"></a>Uygun izinlere sahip bir uygulama dağıtma  
 Bir istemci bilgisayar için bir Windows Forms uygulaması dağıtmanın en yaygın ile yöntemdir [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)], tüm bileşenlerini açıklayan bir dağıtım teknolojisi, uygulamanızın çalıştırılması gerekiyor. [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] derleme ve uygulamayı oluşturan dosyaları açıklamak için bildirimler kullandığı XML dosyalarını çağrılır ve ayrıca, uygulamanızın izinleri gerektirir.  
  
 [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] bir istemci bilgisayarda yükseltilmiş izinleri isteyen iki teknolojiyi sahiptir. Her iki teknolojinin Authenticode sertifikaların kullanımını kullanır. Sertifikaları, uygulamanın güvenilir bir kaynaktan geliyor kullanıcılarınız için bazı güvence yardımcı olur.  
  
 Aşağıdaki tabloda bu teknolojiler açıklanmaktadır.  
  
|Yükseltilmiş izni teknolojisi|Açıklama|  
|------------------------------------|-----------------|  
|İzin yükseltme|Güvenlik iletişim kutusu ilk kez uygulamanızı çalıştığında kullanıcıya sorar. **İzin yükseltme** iletişim kutusu bildirir kullanıcı kimin uygulama yayımlanan hakkında böylece kullanıcı ek güven vermek olup olmadığına dair bilinçli bir karar yapabilirsiniz|  
|Güvenilir uygulama dağıtımı|Bir istemci bilgisayarda bir yayımcının Authenticode sertifikası tek seferlik bir yüklemesini gerçekleştirme bir Sistem Yöneticisi içerir. Bu noktadan itibaren sertifikayla imzalanan uygulamaların kabul olarak güvenilir ve tam güven yerel bilgisayarda ek sormadan çalıştırabilirsiniz.|  
  
 Seçtiğiniz hangi teknoloji dağıtım ortamınıza bağlıdır. Daha fazla bilgi için bkz: [ClickOnce dağıtım stratejisini seçme](/visualstudio/deployment/choosing-a-clickonce-deployment-strategy).  
  
 Varsayılan olarak, [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] ya da Visual Studio kullanarak dağıtılmış uygulamalar veya [!INCLUDE[dnprdnlong](../../../includes/dnprdnlong-md.md)] SDK Araçları (Mage.exe ve MageUI.exe), tam güven sahip bir istemci bilgisayarda çalışması için yapılandırılır. Kısmi güven kullanarak veya yalnızca bazı ek izinler kullanarak uygulamanızı dağıtıyorsanız, bu varsayılanı değiştirmek gerekecektir. Bu da Visual Studio ile yapabileceğiniz veya [!INCLUDE[dnprdnlong](../../../includes/dnprdnlong-md.md)] SDK aracı dağıtımınızı yapılandırdığınızda MageUI.exe. İzlenecek yol MageUI.exe kullanma hakkında daha fazla bilgi için bkz: komut satırından ClickOnce uygulamasını dağıtma.  Ayrıca bkz. [nasıl yapılır: ClickOnce uygulaması için özel izinleri ayarlama](http://msdn.microsoft.com/library/hafybdaa\(v=vs.110\)) veya [nasıl yapılır: ClickOnce uygulaması için özel izinleri ayarlama](http://msdn.microsoft.com/library/hafybdaa\(v=vs.120\)).  
  
 Güvenlik yönlerini hakkında daha fazla bilgi için [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] ve izin yükseltme, bkz: [ClickOnce uygulamalarının güvenliğini sağlama](/visualstudio/deployment/securing-clickonce-applications). Güvenilir uygulama dağıtımı hakkında daha fazla bilgi için bkz: [güvenilir uygulama dağıtımına genel bakış](/visualstudio/deployment/trusted-application-deployment-overview).  
  
### <a name="testing-the-application"></a>Uygulamayı Test Etme  
 Visual Studio kullanarak Windows Forms uygulaması dağıttıysanız, kısmi güven veya kısıtlı izin geliştirme ortamından kümesinin hata ayıklamayı etkinleştirebilirsiniz.  Ayrıca bkz. [nasıl yapılır: sınırlı izinler ile ClickOnce uygulamasında hata ayıklama](http://msdn.microsoft.com/library/593zkfdf\(v=vs.110\)) veya [nasıl yapılır: sınırlı izinler ile ClickOnce uygulamasında hata ayıklama](http://msdn.microsoft.com/library/593zkfdf\(v=vs.120\)).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows Forms Güvenliği](../../../docs/framework/winforms/windows-forms-security.md)  
 [Kod erişim güvenliği temelleri](../../../docs/framework/misc/code-access-security-basics.md)  
 [ClickOnce Güvenliği ve Dağıtımı](/visualstudio/deployment/clickonce-security-and-deployment)  
 [Güvenilir Uygulama Dağıtımına Genel Bakış](/visualstudio/deployment/trusted-application-deployment-overview)  
 [Mage.exe (Bildirim Oluşturma ve Düzenleme Aracı)](../../../docs/framework/tools/mage-exe-manifest-generation-and-editing-tool.md)  
 [MageUI.exe (Bildirim Oluşturma ve Düzenleme Aracı, Grafik İstemci)](../../../docs/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client.md)
