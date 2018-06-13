---
title: '&lt;UseRandomizedStringHashAlgorithm&gt; öğesi'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UseRandomizedStringHashAlgorithm element
- <UseRandomizedStringHashAlgorithm> element
ms.assetid: c08125d6-56cc-4b23-b482-813ff85dc630
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a515c3011905c4f5c18ed9d3e8edf489428c04d8
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32746091"
---
# <a name="ltuserandomizedstringhashalgorithmgt-element"></a>&lt;UseRandomizedStringHashAlgorithm&gt; öğesi
Ortak dil çalışma zamanı üzerinde karma kodlarını dizeleri hesaplar olup olmadığını belirleyen bir uygulama etki alanı temelinde.  
  
 \<Yapılandırma >  
\<çalışma zamanı >  
\<UseRandomizedStringHashAlgorithm >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<UseRandomizedStringHashAlgorithm   
   enabled=0|1 />  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`enabled`|Gerekli öznitelik.<br /><br /> Dizeler için karma kodlarını çubuğunda hesaplanıp hesaplanmayacağını belirler bir uygulama etki alanı temelinde.|  
  
## <a name="enabled-attribute"></a>etkin Öznitelik  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`0`|Ortak dil çalışma zamanı dizeleri için karma kodları üzerinde işlem olmayan bir uygulama etki alanı temelinde; tek bir algoritma dize karma kodlarını hesaplamak için kullanılır. Bu varsayılandır.|  
|`1`|Ortak dil çalışma zamanı üzerinde karma kodlarını dizeleri hesaplar bir uygulama etki alanı temelinde. Farklı uygulama etki alanları ve farklı işlemler aynı dizeleri farklı karma kodlarını olacaktır.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`runtime`|Çalışma zamanı başlatma seçenekleri hakkında bilgi içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Varsayılan olarak, <xref:System.StringComparer> sınıfı ve <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> yöntemi uygulama etki alanları arasında tutarlı karma kodu oluşturan tek bir karma algoritmasını kullanın. Bu ayar için eşdeğerdir `enabled` özniteliği `<UseRandomizedStringHashAlgorithm>` öğesine `0`. Kullanılan karma algoritma budur [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)].  
  
 <xref:System.StringComparer> Sınıfı ve <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> yöntemi de karma kodlarını çubuğunda hesaplar farklı bir karma algoritma kullanın bir uygulama etki alanı temelinde. Sonuç olarak, karma kodlarını eşdeğer dizeleri için uygulama etki alanları arasında farklılık gösterir. Bu bir katılımı özelliğidir; Bunu yararlanmak için ayarlamalısınız `enabled` özniteliği `<UseRandomizedStringHashAlgorithm>` öğesine `1`.  
  
 Bir karma tablosu dize aramada genellikle bir O(1) işlemdir. Ancak, çok sayıda çakışma oluştuğunda, arama O olabilir (n<sup>2</sup>) işlemi. Kullanabileceğiniz `<UseRandomizedStringHashAlgorithm>` rastgele bir karma algoritma başına içinden karma kodlarını hesaplanır anahtarlar veri giriş, özellikle dayanır bağlandığınızda sırayla olası çakışmaları sayısını sınırlar, uygulama etki alanı oluşturmak için yapılandırma öğesi kullanıcılar tarafından.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek tanımlayan bir `DisplayString` özel dize sabiti içeren sınıf `s`, değeri olan "Dize budur." Ayrıca içeren bir `ShowStringHashCode` dize değeri ve karma kodunu içinde yöntemi Yürütülüyor uygulama etki alanı adı ile birlikte görüntüler yöntemi.  
  
 [!code-csharp[System.String.GetHashCode#2](../../../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.String.GetHashCode/CS/perdomain.cs#2)]
 [!code-vb[System.String.GetHashCode#2](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.String.GetHashCode/VB/perdomain.vb#2)]  
  
 Örnek bir yapılandırma dosyası girmeden çalıştırdığınızda, aşağıdakine benzer bir çıktı görüntüler. Karma kodlarını dize için iki uygulama etki alanları aynı olduğunu unutmayın.  
  
```  
String 'This is a string.' in domain 'PerDomain.exe': 941BCEAC  
String 'This is a string.' in domain 'NewDomain': 941BCEAC  
```  
  
 Ancak, örneğin dizinine aşağıdaki yapılandırma dosyası ekleyin ve ardından örnek çalıştırırsanız, karma kodlarını aynı dize için uygulama etki alanına göre farklılık gösterir.  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
   <runtime>  
      <UseRandomizedStringHashAlgorithm enabled="1" />  
   </runtime>  
</configuration>  
```  
  
 Yapılandırma dosyası mevcut olduğunda, aşağıdaki çıktı örneği görüntüler:  
  
```  
String 'This is a string.' in domain 'PerDomain.exe': 5435776D  
String 'This is a string.' in domain 'NewDomain': 75CC8236  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType>  
 <xref:System.String.GetHashCode%2A?displayProperty=nameWithType>  
 <xref:System.Object.GetHashCode%2A?displayProperty=nameWithType>
