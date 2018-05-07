---
title: Güvenliği Saydam Kod
ms.date: 03/30/2017
helpviewer_keywords:
- transparent code
- security-transparent code
ms.assetid: 4f3dd841-82f7-4659-aab0-6d2db2166c65
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6a491a87c896c76fa62f1702d1ef0e99fc404607
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="security-transparent-code"></a>Güvenliği Saydam Kod
<a name="top"></a>
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 Güvenlik üç etkileşen parça içerir: Korumalı alan, izinler ve zorlama. Korumalı alan uygulama olarak bazı kodlar burada tam olarak güvenilir ve diğer kod korumalı alanı ayarlamak grant izinler sınırlandırılır olarak kabul edilir yalıtılmış etki alanları oluşturma ifade eder. Korumalı alan grant kümesinde çalışan uygulama kodu saydam olarak kabul edilir; diğer bir deyişle, güvenlik etkileyebilecek herhangi bir işlem gerçekleştirilemiyor. Korumalı alan bulgu göre belirlenir ayarlamanız verin (<xref:System.Security.Policy.Evidence> sınıfı). Kanıt hangi belirli izinleri tarafından korumalı alanlar gereklidir ve ne tür sanal oluşturulabilir tanımlar. Saydam kod yalnızca verme kümesi içinde yürütmesine izin vermek üzere zorlama başvuruyor.  
  
> [!IMPORTANT]
>  Güvenlik İlkesi .NET Framework'ün önceki sürümlerinde anahtar öğesi oluştu. İle başlayarak [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], güvenlik ilkesi artık kullanılmıyor. Güvenlik İlkesi eleme güvenlik saydamlık ' ayrıdır. Bu değişikliğin etkilerini hakkında daha fazla bilgi için bkz: [kod erişimi güvenlik ilkesi uyumluluğu ve geçiş](../../../docs/framework/misc/code-access-security-policy-compatibility-and-migration.md).  
  
 Bu konuda daha fazla ayrıntı saydamlık modelinde açıklanmaktadır. Aşağıdaki bölümleri içerir:  
  
-   [Saydamlık modeli amacı](#purpose)  
  
-   [Saydamlık düzeyi belirtme](#level)  
  
-   [Saydamlık zorlama](#enforcement)  
  
<a name="purpose"></a>   
## <a name="purpose-of-the-transparency-model"></a>Saydamlık Modelinin Amacı  
 Saydamlık altyapısının bir parçası olarak çalışan bir kod uygulamasından bir parçası olarak çalışan bir kod ayıran bir zorlama mekanizmasıdır. Saydamlık yerel kodu çağırma gibi ayrıcalıklı (kritik kod) şeyler yapabilir kodu ve (saydam kod) edemiyor kodu arasında bir engel çizer. Saydam kod, işletim izin kümesi sınırları içinde komutları yürütün ancak yapılamıyor yürütmek, öğesinden türetilen veya kritik kod içerir.  
  
 Saydamlık zorlama birincil amacı ayrıcalığına dayalı kodunun farklı gruplar yalıtmak için basit ve etkili bir mekanizma sağlamaktır. Bu ayrıcalık grupları korumalı alan modeli bağlamında olan tam olarak güvenilir (diğer bir deyişle, değil sınırlıdır) veya kısmen güvenilen (diğer bir deyişle, verilen korumalı alanda izni sınırlı).  
  
> [!IMPORTANT]
>  Saydamlık model kod erişim güvenliği aşıyor. Saydamlık tam zamanı derleyici tarafından zorlanır ve tam güven içeren bir derlemenin için ayarlanmış grant bakılmaksızın yürürlükte kalır.  
  
 Saydamlık .NET Framework 2.0 sürümünde güvenlik modeli kolaylaştırmak ve yazma ve güvenli kitaplıkları ve uygulamaları dağıtmak kolaylaştırmak için sunulmuştur. Saydam kod, Microsoft Silverlight kısmen güvenilir uygulamalar geliştirme işlemini basitleştirmek için de kullanılır.  
  
> [!NOTE]
>  Kısmen güvenilir uygulama geliştirirken, hedef konaklar için izin gereksinimleri farkında olması gerekir. Bazı ana bilgisayarlar tarafından izin verilmeyen kaynaklara kullanan bir uygulama geliştirebilirsiniz. Bu uygulama hatasız derlenir ancak barındırılan ortama yüklendiğinde başarısız olur. Visual Studio kullanarak uygulamanızı geliştirdiyseniz, kısmi güven veya kısıtlı izin geliştirme ortamından kümesinin hata ayıklamayı etkinleştirebilirsiniz. Daha fazla bilgi için bkz: [nasıl yapılır: sınırlı izinler ile ClickOnce uygulamasında hata ayıklama](/visualstudio/deployment/how-to-debug-a-clickonce-application-with-restricted-permissions). ClickOnce uygulamaları için sağlanan hesaplamak izinleri özellik de kısmen güvenilen her uygulama için kullanılabilir.  
  
 [Başa dön](#top)  
  
<a name="level"></a>   
## <a name="specifying-the-transparency-level"></a>Saydamlık Düzeyini Belirtme  
 Derleme düzeyi <xref:System.Security.SecurityRulesAttribute> özniteliği açıkça seçer <xref:System.Security.SecurityRuleSet> derleme izleyeceği kuralları. Kuralları nerede yüksek düzeylerden daha sıkı zorlama güvenlik kuralları anlamına sayısal düzey altındaki bir sistemin, düzenlenir.  
  
 Düzeyleri aşağıdaki gibidir:  
  
-   Düzey 2 (<xref:System.Security.SecurityRuleSet.Level2>) – [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] saydamlık kuralları.  
  
-   Düzey 1 (<xref:System.Security.SecurityRuleSet.Level1>) – .NET Framework 2.0 saydamlık kuralları.  
  
 İki saydamlık düzeyleri arasındaki birincil fark düzey 1 derleme dışına gelen çağrıları için saydamlığı kuralları uygulamaz ve yalnızca uyumluluk için kullanılması amaçlanmıştır ' dir.  
  
> [!IMPORTANT]
>  Yalnızca uyumluluk düzeyi 1 saydamlığını belirtmeniz gerekir; diğer bir deyişle, kullanan .NET Framework 3.5 veya daha önceki geliştirilen yalnızca kodu için 1 düzeyini belirtmek <xref:System.Security.AllowPartiallyTrustedCallersAttribute> özniteliği veya saydamlık modelini kullanmıyor. Örneğin, düzey 1 saydamlık kısmen güvenilen arayanlara (APTCA) gelen çağrıları izin .NET Framework 2.0 derlemeler için kullanın. İçin geliştirilen kodu [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], Düzey 2 saydamlık her zaman kullanın.  
  
### <a name="level-2-transparency"></a>Düzey 2 saydamlık  
 Düzey 2 saydamlık sunulmuştur [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]. Bu modelin üç tenets şunlardır: saydam kod, güvenlik açısından güvenli-kritik kod ve güvenlik açısından kritik kod.  
  
-   (Tam güven dahil), verilen izinlere bakılmaksızın saydam kod, yalnızca diğer saydam kod veya güvenlik açısından güvenli-kritik kod çağırabilir. Kısmen güvenilen kodu ise, yalnızca etki alanının izin kümesi tarafından izin verilen eylemleri gerçekleştirebilirsiniz. Saydam kod aşağıdakileri yapamazsınız:  
  
    -   Gerçekleştirmek bir <xref:System.Security.CodeAccessPermission.Assert%2A> işlemi veya ayrıcalık yükseltme.  
  
    -   Güvenli olmayan veya doğrulanamayan kodu içerir.  
  
    -   Doğrudan kritik kod çağırabilir.  
  
    -   Yerel kod ya da sahip code <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> özniteliği.  
  
    -   Tarafından korunan bir üye çağırın bir <xref:System.Security.Permissions.SecurityAction.LinkDemand>.  
  
    -   Kritik türlerinden devralır.  
  
     Ayrıca, saydam yöntemler kritik sanal yöntemleri geçersiz kılmak veya kritik arabirim yöntemleri uygulayın.  
  
-   Güvenlik açısından güvenli-kritik kodu tam olarak güvenilmeyen ancak saydam kod tarafından çağrılabilir. Tam güven kodunun sınırlı bir yüzey alanını gösterir. Doğruluk ve güvenlik Doğrulamalar güvenli kritik kodda gerçekleşir.  
  
-   Güvenlik açısından kritik kod herhangi bir kod çağırabilir ve tam olarak güvenilmeyen ancak tarafından saydam kod çağrılamaz.  
  
### <a name="level-1-transparency"></a>Düzey 1 Saydamlık  
 Düzey 1 saydamlık modeli güvenlik denetim tabi olan kod miktarını azaltmak, geliştiricilerin için .NET Framework sürüm 2.0 sunulmuştur. Düzey 1 saydamlık sürüm 2.0 genel kullanıma açık olsa da, öncelikle yalnızca Microsoft güvenlik denetim amacıyla kullanılan. Ek açıklamalar, aracılığıyla geliştiricilerin hangi türlerinizi sağlayabilir ve üyeleri güvenlik yükseltmeleri ve (güvenlik açısından kritik) güvenilen başka eylemler gerçekleştirebilir ve hangi (güvenlik saydam) olamaz. Saydam olarak tanımlanan kod güvenlik denetimi, yüksek derecede gerektirmez. Düzey 1 saydamlık saydamlık zorlama derlemede sınırlı olduğunu belirtir. Diğer bir deyişle, herhangi bir genel türleri veya güvenlik açısından kritik olarak tanımlanır üyeleri yalnızca derlemede güvenlik açısından kritik. Bunlar gelen derlemenin dışından çağrıldığında bu türleri ve üyeleri için güvenlik zorlamak istiyorsanız, bağlantı talepleri tam güven için kullanmanız gerekir. Bunu yapmazsanız, herkese görünür güvenlik kritik türleri ve üyeleri güvenlik-güvenli-kritik olarak kabul edilir ve derleme dışına kısmen güvenilen kod tarafından çağrılabilir.  
  
 Düzey 1 saydamlık modeli aşağıdaki sınırlamalara sahiptir:  
  
-   Güvenliği saydam kod güvenlik kritik türleri ve ortak üyeler erişilebilir.  
  
-   Saydamlık ek açıklamalar yalnızca bir derlemenin içinde uygulanır.  
  
-   Güvenlik açısından kritik türleri ve üyeleri bağlantı talepleri derleme dışına gelen çağrıları için güvenlik zorlamak için kullanmanız gerekir.  
  
-   Devralma kuralları zorunlu tutulmaz.  
  
-   Tam güvende çalıştırdığınızda zararlı işlemler yapmak saydam kod olasılığı vardır.  
  
 [Başa dön](#top)  
  
<a name="enforcement"></a>   
## <a name="transparency-enforcement"></a>Saydamlığı Zorlama  
 Saydamlık hesaplanan kadar saydamlık kuralları zorunlu tutulmaz. Bu sırada, bir <xref:System.InvalidOperationException> saydamlık kuralı ihlal edilirse atılır. Saydamlık hesaplanan süre birden çok etkene bağlıdır ve tahmin edilemez. Mümkün olduğunca geç hesaplanır. İçinde [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], derleme düzeyi saydamlık hesaplamanın .NET Framework 2. 0 ' daha çabuk. Saydamlık hesaplamanın gerektiğinde zamanına göre yapılacağını tek garantisi yoktur. Bu, nasıl tam zamanında (JIT) derleyici noktayı bir yöntem derlenir ve bu yöntem herhangi bir hata algılandığında değiştirebilirsiniz için benzer. Saydamlık hesaplaması kodunuzu saydamlık hataları yoksa görünmez olur.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Güvenliği saydam kod, düzey 1](../../../docs/framework/misc/security-transparent-code-level-1.md)  
 [Güvenliği saydam kod, Düzey 2](../../../docs/framework/misc/security-transparent-code-level-2.md)
