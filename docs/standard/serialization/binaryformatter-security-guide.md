---
title: BinaryFormatter Güvenlik Kılavuzu
description: Bu makalede, BinaryFormatter türünde devralınan güvenlik riskleri ve farklı serileştiricilerin kullanması için öneriler açıklanmaktadır.
ms.date: 07/11/2020
ms.author: levib
author: GrabYourPitchforks
ms.openlocfilehash: f6a54b34bbf1e19212fe37aadb448a1722fe9ff0
ms.sourcegitcommit: 2543a78be6e246aa010a01decf58889de53d1636
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/17/2020
ms.locfileid: "86444768"
---
# <a name="binaryformatter-security-guide"></a>BinaryFormatter Güvenlik Kılavuzu

Bu makale aşağıdaki .NET uygulamalarına yöneliktir:

* Tüm sürümleri .NET Framework
* .NET Core 2,1-3,1
* .NET 5,0 ve üzeri

## <a name="background"></a>Arka Plan

> [!WARNING]
> <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>Tür tehlikelidir ve veri işleme için ***not*** önerilmez. Uygulamalar `BinaryFormatter` , işlemekte oldukları verilerin güvenilir olmasını düşünse bile, en kısa sürede kullanılması gerekir. `BinaryFormatter`güvenli olmayan bir güvenlik yapılamaz.

Bu makale aşağıdaki türler için de geçerlidir:

* <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>
* <xref:System.Runtime.Serialization.NetDataContractSerializer>
* <xref:System.Web.UI.LosFormatter>
* <xref:System.Web.UI.ObjectStateFormatter>

Seri kaldırma güvenlik açıkları, istek yüklerinin güvenli bir şekilde işlendiği bir tehdit kategorisidir. Bir uygulamaya karşı bu güvenlik açıklarından yararlanan bir saldırgan, hedef uygulama içinde hizmet reddi (DoS), bilgilerin açığa çıkması veya uzaktan kod yürütülmesine neden olabilir. Bu risk kategorisi sürekli olarak [OWASP en iyi 10](https://owasp.org/www-project-top-ten/)' un olmasını sağlar. Hedefler, C/C++, Java ve C# dahil olmak üzere [çeşitli dillerde](https://owasp.org/www-community/vulnerabilities/Deserialization_of_untrusted_data)yazılmış uygulamaları içerir.

.NET sürümünde en büyük risk hedefi, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> veri serisini kaldırmak için türünü kullanan uygulamalardır. `BinaryFormatter`, gücü ve kullanım kolaylığı nedeniyle .NET ekosistemi genelinde yaygın olarak kullanılır. Ancak, bu aynı güç, saldırganların hedef uygulama içindeki denetim akışını etkilebilme yeteneği sağlar. Başarılı saldırılar, saldırganın hedef işlem bağlamında kod çalıştırabilmesini sağlayabilir.

Daha basit bir benzerleme vurguladı olarak, `BinaryFormatter.Deserialize` yük üzerinde çağırmanın bu yükü tek başına yürütülebilir dosya olarak yorumlayarak ve başlatarak buna eşdeğer olduğunu varsayalım.

## <a name="binaryformatter-security-vulnerabilities"></a>BinaryFormatter güvenlik güvenlik açıkları

> [!WARNING]
> `BinaryFormatter.Deserialize`Güvenilir olmayan girişle kullanıldığında Yöntem __hiçbir zaman__ güvenli değildir. Bunun yerine, bu makalede daha sonra özetlenen alternatifden birini kullanmayı öneririz.

`BinaryFormatter`seri durumdan çıkarma güvenlik açıkları iyi anlaşılmış bir tehdit kategorisi olacak şekilde uygulandı. Sonuç olarak, kod modern en iyi uygulamaları izlemez. `Deserialize`Yöntemi, saldırganların uygulamalara yönelik DOS saldırıları gerçekleştirmesini sağlamak için bir vektör olarak kullanılabilir. Bu saldırılar, uygulamanın yanıt vermemesine veya beklenmeyen işlem sonlandırmasıyla sonuçlanır. Bu saldırı kategorisi bir `SerializationBinder` veya başka bir `BinaryFormatter` yapılandırma anahtarıyla azaltılamaz. .NET bu davranışı ***tasarıma göre*** kabul eder ve davranışı değiştirmek için bir kod güncelleştirmesi yayınlamayın.

`BinaryFormatter.Deserialize`, bilgilerin açığa çıkması veya uzaktan kod yürütme gibi diğer saldırı kategorilerine karşı savunmasız olabilir. Özel gibi özelliklerin kullanılması <xref:System.Runtime.Serialization.SerializationBinder> , bu riskleri doğru şekilde azaltmak için yetersiz olabilir. Bu olasılık, .NET 'in bir güvenlik güncelleştirmesini önemli bir şekilde yayımlayamayacak bir nobir güvenlik açığının bulunmasından oluşur. Tüketiciler, bağımsız senaryolarını değerlendirmeli ve bu risklerle ilgili olası pozlandırmayı göz önünde bulundurmalıdır.

`BinaryFormatter`Tüketicilerin uygulamalarında tek tek risk değerlendirmesi gerçekleştirmesini öneririz. Bunun kullanılması gerekip gerekmediğini belirlemede tüketicinin tek sorumluluğudur `BinaryFormatter` . Tüketiciler, kullanmanın güvenlik, teknik, saygınlık, yasal ve mevzuat gereksinimlerini değerlendirmelidir `BinaryFormatter` .

## <a name="preferred-alternatives"></a>Tercih edilen alternatifler

.NET, güvenilir olmayan verileri güvenli bir şekilde işleyebilen çeşitli yerleşik serileştiriciler sunar:

* <xref:System.Xml.Serialization.XmlSerializer>ve <xref:System.Runtime.Serialization.DataContractSerializer> nesne grafiklerini XML içine ve XML 'den seri hale getirme. `DataContractSerializer`İle karıştırmayın <xref:System.Runtime.Serialization.NetDataContractSerializer> .
* <xref:System.IO.BinaryReader>ve <xref:System.IO.BinaryWriter> for xml ve JSON.
* <xref:System.Text.Json>Nesne GRAFIKLERINI JSON içine serileştirme API 'leri.

## <a name="dangerous-alternatives"></a>Tehlikeli alternatifler

Aşağıdaki serileştiricilerle önleyin:

* <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>
* <xref:System.Web.UI.LosFormatter>
* <xref:System.Runtime.Serialization.NetDataContractSerializer>
* <xref:System.Web.UI.ObjectStateFormatter>

Önceki serileştiricilerin hepsi gibi Kısıtlamasız çok biçimli seri hale getirmeleri ve tehlikeli olması yeterlidir `BinaryFormatter` .

## <a name="the-risks-of-assuming-data-to-be-trustworthy"></a>Verilerin güvenilir olmasını kabul etmek için riskler

Genellikle, bir uygulama geliştiricisi yalnızca güvenilen girişi işlediklerinden emin olabilirler. Güvenli giriş durumu nadir bazı durumlarda geçerlidir. Ancak, bir yükün geliştirici tarafından gerçekleşmeksizin bir güven sınırını kesişimi çok daha yaygındır.

Çalışanların iş istasyonlarından bir masaüstü istemcisini hizmet ile etkileşimde bulunmak üzere kullanması için bir __Şirket içi sunucu düşünün__ . Bu senaryo, kullanmanın kabul edilebilir olduğu "güvenli" bir kurulum olarak naïvely görünebilir `BinaryFormatter` . Ancak, bu senaryo, kuruluş genelinde yayılabilecek tek bir çalışanın makinesine erişim elde eden kötü amaçlı yazılım için bir vektör sunar. Bu kötü amaçlı yazılım, `BinaryFormatter` çalışanın iş istasyonundan arka uç sunucusuna geçici olarak taşımak için kuruluşun kullanım özelliğinden yararlanabilir. Daha sonra şirketin hassas verilerini alabilir. Bu tür veriler, ticari gizlilikler veya müşteri verileri içerebilir.

__Ayrıca, `BinaryFormatter` kaydetme durumunu sürdürmek için kullanan bir uygulamayı da göz önünde bulundurun.__ Bu, ilk olarak güvenli bir senaryo gibi görünse de, kendi sabit sürücünüzde veri okuma ve yazma, küçük bir tehdidi temsil ediyor olabilir. Ancak, belgeleri e-posta veya Internet üzerinden paylaşmak yaygındır ve çoğu Son Kullanıcı bu indirilen dosyaları riskli davranış olarak açmayı engellemez.

Bu senaryo, nefarli etkiye yararlanılabilir olabilir. Uygulama bir oyunsa, kaydetme dosyalarını paylaşan kullanıcılar kendilerini riske önünde yerleştirir. Geliştiricilerin kendisi de hedeflenebilir. Saldırgan, geliştiricilerin teknik desteğini e-posta ile bir kötü amaçlı veri dosyası ekleyerek ve destek personelinden bunu açmasını istiyor olabilir. Bu tür bir saldırı, saldırgana kuruluşta bir saldırgan yaşına verebilir.

Veri dosyasının Bulut depolamada depolandığı ve Kullanıcı makineleri arasında otomatik olarak eşitlendiği başka bir senaryo vardır. Bulut depolama hesabına erişim elde edebilen bir saldırgan veri dosyasını zarar verebilir. Bu veri dosyası otomatik olarak kullanıcının makinelerine eşitlenir. Kullanıcının veri dosyasını bir dahaki açtığı bir sonraki sefer, saldırganın yükü çalışır. Böylece saldırgan, tam kod yürütme izinleri kazanmak için bir bulut depolama hesabı güvenliğinin aşılmasına neden olabilir.

__Masaüstü yüklemesi modelinden bir bulut ilk modeline taşınan bir uygulama düşünün.__ Bu senaryo, bir masaüstü uygulamasından veya zengin istemci modelinden Web tabanlı bir modele geçiş yapan uygulamaları içerir. Masaüstü uygulaması için çizilen tüm tehdit modelleri, bulut tabanlı hizmet için geçerli değildir. Masaüstü uygulaması için tehdit modeli, "istemcinin kendi saldırılarına karşı ilginç değil" gibi belirli bir tehdidi kapatabilir. Ancak aynı tehdit, uzak bir kullanıcının (istemci) bulut hizmeti 'nin kendisine saldırmasını düşündüğünde ilginç hale gelebilir.

> [!NOTE]
> Genel koşullarda, serileştirme amacı bir uygulamayı bir uygulamanın içine veya dışına aktarmaktır. Tehdit modelleme alıştırması, neredeyse her zaman bir güven sınırını aşan bu tür veri aktarımını işaretler.

## <a name="further-resources"></a>Daha fazla kaynak

* [YSoSerial.net](https://github.com/pwntester/ysoserial.net) tarafından kullanılan uygulamaların nasıl saldırıya alınacağını araştırın `BinaryFormatter` .
* Tehdit modelleme uygulamaları ve hizmetleri hakkında bilgi için [tehdit modelleme](/securityengineering/sdl/threatmodeling) .
* Seri kaldırma güvenlik açıkları genel arka planı:
  * [OWASP Top 10-A8:2017-güvensiz serisini kaldırma](https://owasp.org/www-project-top-ten/OWASP_Top_Ten_2017/Top_10-2017_A8-Insecure_Deserialization)
  * [CWE-502: güvenilmeyen verilerin serisini kaldırma](https://cwe.mitre.org/data/definitions/502.html)
