---
title: Kullanım kuralları (kod analizi)
description: Kod Analizi kullanım kuralları hakkında bilgi edinin.
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.usagerules
helpviewer_keywords:
- rules, usage
- managed code analysis rules, usage rules
- usage rules
author: gewarren
ms.author: gewarren
ms.openlocfilehash: c8b14d2f92502d5a82e41a322e599745bdcf8b85
ms.sourcegitcommit: a6bd4cad438fe479cbd112eae10f2cd449f06e40
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/08/2020
ms.locfileid: "96589649"
---
# <a name="usage-rules"></a>Kullanım kuralları

Kullanım kuralları, .NET 'in uygun kullanımını destekler.

## <a name="in-this-section"></a>Bu bölümde

|Kural|Açıklama|
|----------|-----------------|
|[CA1801: Kullanılmayan parametreleri gözden geçirin](ca1801.md)|Yöntem imzası, yöntemin gövdesinde kullanılmayan bir parametre içerir.|
|[CA1816: GC.SuppressFinalize'ı doğru çağırın](ca1816.md)|Dispose uygulamasının bir yöntemi çağırmaz `GC.SuppressFinalize` ; ya da çağrıların uygulanması olmayan bir yöntem `Dispose` `GC.SuppressFinalize` ya da bir yöntem, `GC.SuppressFinalize` `this` (Visual Basic) dışında bir öğe çağırır ve geçirir `Me` .|
|[CA2200: Yığın ayrıntılarını korumak için yeniden fırlatın](ca2200.md)|Tekrar fırlatılan bir özel durum ve fırlatma açıklamasında açıkça belirtilen özel durum. Bir özel durum throw deyiminde özel durum belirterek yeniden fırlatılırsa yöntem listesi özel durum döndüren özgün yöntem ile kaybolan geçerli yöntem arasında çağırır.|
|[CA2201: Ayrılmış özel durum türlerini harekete geçirmeyin](ca2201.md)|Bu, özgün hatayı algılamaya ve hata ayıklamasına keskin hale getirir.|
|[CA2207: Değer türü statik alanları satır içi başlatın](ca2207.md)|Bir değer türü açık bir statik oluşturucu bildirir. Bu kural ihlalini düzeltmek için bildirildiğinde, tüm statik veriyi başlatın ve statik oluşturucuyu kaldırın.|
|[CA2208: Bağımsız değişken özel durumlarını doğru örnekleyin](ca2208.md)|Varsayılan (parametresiz) kurucu veya ArgumentException türeyen özel bir durum türü için çağrı yapılır veya hatalı dize bağımsız değişkeni parametreli bir kurucu veya ArgumentException türeyen bir özel durum türü iletilir.|
|[CA2211: Sabit olmayan alanlar görünür olmamalıdır](ca2211.md)|Sabit veya salt okuma olmayan statik alanlar iş parçacığı açısından güvenli değildir. Bu tür bir alana erişimin dikkatle denetlenmesi ve sınıf nesnesine erişimin eşitlenmesi için gelişmiş programlama teknikleri olması gerekir.|
|[CA2213: Atılabilen alanlar atılmalıdır](ca2213.md)|Uygulayan bir tür <xref:System.IDisposable?displayProperty=fullName> , de uygulayan türler olan alanları bildirir `IDisposable` . `Dispose`Alan yöntemi, `Dispose` bildirim türünün yöntemi tarafından çağrılmaz.|
|[CA2214: Geçersiz kılınabilir metotları oluşturucular içinde çağırmayın](ca2214.md)|Bir Oluşturucu sanal bir yöntemi çağırdığında, yöntemi çağıran örnek için olan oluşturucunun yürütülmemiş olması mümkündür.|
|[CA2215: Atma metotları taban sınıf atmayı çağırmalıdır](ca2215.md)|Bir tür atılabilir bir türden devralırsa, `Dispose` kendi yönteminden temel tür yöntemini çağırmalıdır `Dispose` .|
|[CA2216: Atılabilir türler sonlandırıcıyı bildirmelidir](ca2216.md)|Uygulayan <xref:System.IDisposable?displayProperty=fullName> ve yönetilmeyen kaynakların kullanımını öneren alanlar içeren bir tür, tarafından açıklandığı şekilde sonlandırıcıyı uygulamaz `Object.Finalize` .|
|[CA2217: Sabit listelerini FlagsAttribute ile işaretlemeyin](ca2217.md)|Dışarıdan görünür bir sabit listesi ile işaretlenir `FlagsAttribute` ve Numaralandırmadaki bir veya daha fazla değere sahip olan bir ya da daha fazla değere sahiptir.|
|[CA2218: GetHashCode'u Eşittir'i geçersiz kılarak geçersiz kılın](ca2218.md)|Ortak tür geçersiz kılınır <xref:System.Object.Equals%2A?displayProperty=fullName> ancak geçersiz kılınmaz <xref:System.Object.GetHashCode%2A?displayProperty=fullName> .|
|[CA2219: Özel durum yan tümceleri içinde özel durum harekete geçirmeyin](ca2219.md)|Bir istisna sonlandırıcı ya da arıza yan tümcesine neden olduğunda, yeni istisna aktif istisnayı saklar. Filtre yan tümcesinde bir özel durum ortaya çıktığında, çalışma zamanı özel durumu sessizce yakalar. Bu, özgün hatayı algılamaya ve hata ayıklamasına keskin hale getirir.|
|[CA2224: Eşittir işlecini aşırı yüklerken Equals'ı geçersiz kılın](ca2224.md)|Ortak tür eşitlik işlecini uygular, ancak geçersiz kılmaz <xref:System.Object.Equals%2A?displayProperty=fullName> .|
|[CA2225: İşleç aşırı yüklemeleri adlandırılmış alternatiflere sahiptir](ca2225.md)|Operatör aşırı yüklemesi bulundu ve beklenen adlandırılmış alternatif yöntem bulunamadı. Adlandırılmış alternatif üye, işleçle aynı işlevselliğe erişim sağlar ve aşırı yüklenmiş işleçleri desteklemeyen dillerde programlayan geliştiriciler için sağlanır.|
|[CA2226: İşleçler simetrik aşırı yüklemelere sahip olmalıdır](ca2226.md)|Bir tür eşitlik veya eşitsizlik işlecini uygular ve karşıt işleci uygulamaz.|
|[CA2227: Koleksiyon özellikleri salt okunur olmalıdır](ca2227.md)|Yazılabilir koleksiyon özelliği kullanıcının koleksiyonun tamamını farklı bir koleksiyonla değiştirmesine izin verir. Salt okunur özelliği değiştirilmesini durdurur ancak yine de tekil üyelerin ayarlamasına izin verir.|
|[CA2229: Serileştirme oluşturucularını uygulayın](ca2229.md)|Bu kural ihlalini düzeltmek için seri hale getirme yapıcısını uygular. Kapalı bir sınıf için kurucusunu özel yapın; aksi takdirde korunmuş yapın.|
|[CA2231: Eşittir işlecini ValueType.Equals'ı geçersiz kılarak aşırı yükleyin](ca2231.md)|Değer türü geçersiz kılınır `Object.Equals` ancak eşitlik işlecini uygulamaz.|
|[CA2234: Dizeler yerine System.Uri nesneleri gönderin](ca2234.md)|Adında "URI", "URI", "urn", "urn", "url" veya "url" içeren bir dize parametresi olan yöntem çağrısı yapıldı.  Metodun bildirim türü, parametresine sahip karşılık gelen bir yöntem aşırı yüklemesini içerir <xref:System.Uri?displayProperty=fullName> .|
|[CA2235: Tüm serileştirilebilir olmayan alanları işaretleyin](ca2235.md)|Seri hale getirilemeyen bir örnek alan türü seri hale getirilebilir bir tür içinde bildirilir.|
|[CA2237: ISerializable türleri SerializableAttribute ile işaretleyin](ca2237.md)|Ortak dil çalışma zamanı tarafından seri hale getirilebilir olarak tanınmak için, türün, arabirimin uygulanmasıyla özel bir serileştirme yordamı kullanması durumunda bile, türlerin SerializableAttribute özniteliğiyle işaretlenmesi gerekir `ISerializable` .|
|[CA2241: Biçimlendirme metotlarına doğru bağımsız değişkenleri sağlayın](ca2241.md)|Geçirilen biçim bağımsız değişkeni, <xref:System.String.Format%2A?displayProperty=nameWithType> her nesne bağımsız değişkenine karşılık gelen bir biçim öğesi içermez veya tam tersi de geçerlidir.|
|[CA2242: NaN için doğru test edin](ca2242.md)|Bu ifade, veya ile karşı bir değeri sınar `Single.Nan` `Double.Nan` . `Single.IsNan(Single)` `Double.IsNan(Double)` Değerini test etmek için veya kullanın.|
|[CA2243: Öznitelik dize harfleri doğru çözümlenmelidir](ca2243.md)|Özniteliğin dize sabit değeri bir URL, GUID veya sürüm için doğru ayrıştırılmadı.|
|[CA2244: Dizine eklenmiş öğe başlatmalarını yineleme](ca2244.md)|Bir nesne başlatıcısının aynı sabit dizine sahip birden fazla dizinli öğe başlatıcısı vardır. Son başlatıcı gereksizdir.|
|[CA2245: Bir özelliği kendisine atama](ca2245.md)|Bir özellik yanlışlıkla kendisine atandı.|
|[CA2246: Sembol ve üyesini aynı deyime atama](ca2246.md)|Bir sembol ve üyesini atama, diğer bir deyişle, bir alan veya özellik, aynı deyimde önerilmez. Üye erişiminin, bu deyimdeki atamadan önce simgenin eski değerini veya atamasından yeni değeri kullanması amaçlandıysa, bu, net değildir.|
|[CA2247: TaskCompletionSource oluşturucusuna geçirilen bağımsız değişken TaskContinuationOptions sabit listesi yerine TaskCreationOptions sabit listesi olmalı](ca2246.md)|TaskCompletionSource, temel alınan görevi denetleyen TaskCreationOptions ve görevde saklanan nesne durumunu alan oluşturucuların bulunduğu oluşturuculara sahiptir.  TaskCreationOptions yerine bir TaskContinuationOptions 'ı yanlışlıkla geçirmek, çağrının durum olarak kabul edilmesine neden olur.|
|[CA2248: ' Enum. HasFlag ' için doğru ' Enum ' bağımsız değişkenini sağlayın](ca2248.md)|Yöntem çağrısına bir bağımsız değişken olarak geçirilen sabit listesi türü, `HasFlag` çağıran enum türünden farklı.|
|[CA2249: String.IndexOf yerine String.Contains kullanmayı düşünün](ca2249.md)|`string.IndexOf`Sonucun varlığı veya bir alt dizenin yokluğunu denetlemek için kullanıldığı yere yapılan çağrılar, ile değiştirilebilir `string.Contains` .|
