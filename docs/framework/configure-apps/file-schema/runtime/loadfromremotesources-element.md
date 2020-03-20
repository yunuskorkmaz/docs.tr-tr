---
title: <loadFromRemoteSources> Öğesi
ms.date: 05/24/2018
helpviewer_keywords:
- loadFromRemoteSources element
- <loadFromRemoteSources> element
ms.assetid: 006d1280-2ac3-4db6-a984-a3d4e275046a
ms.openlocfilehash: a0dcffe378cdd09de0fbd8f0a6ef0635c033fd9c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154068"
---
# <a name="loadfromremotesources-element"></a>\<loadFromRemoteSources> elemanı
Uzak kaynaklardan yüklenen derlemelerin .NET Framework 4 ve sonraki lerine tam güven verilip verilmemesi gerektiğini belirtir.
  
> [!NOTE]
> Visual Studio proje hata listesindeki bir hata iletisi veya yapı hatası nedeniyle bu makaleye yönlendirildiyseniz, [bkz.](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ee890038(v=vs.100))  
  
[**\<yapılandırma>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<çalışma zamanı>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<loadFromRemoteSources>**  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<loadFromRemoteSources
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve öğeler
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`enabled`|Gerekli öznitelik.<br /><br /> Uzak bir kaynaktan yüklenen bir derlemeye tam güven verilip verilmemesi gerektiğini belirtir.|  
  
## <a name="enabled-attribute"></a>etkin öznitelik  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`false`|Uzak kaynaklardan gelen uygulamalara tam güven vermeyin. Bu varsayılandır.|  
|`true`|Uzak kaynaklardan gelen uygulamalara tam güven tanıyın.|  
  
### <a name="child-elements"></a>Alt öğeleri  
 Yok.  
  
### <a name="parent-elements"></a>Üst öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`runtime`|Çalışma zamanı başlatma seçenekleri hakkında bilgi içerir.|  
  
## <a name="remarks"></a>Açıklamalar

.NET Framework 3.5 ve önceki sürümlerinde, bir derlemeyi uzak bir konumdan yüklerseniz, derlemedeki kod, yüklendiği bölgeye bağlı bir hibe kümesiyle kısmi güven içinde çalışır. Örneğin, bir web sitesinden bir derleme yüklerseniz, internet bölgesine yüklenir ve Internet izin kümesi verilir. Başka bir deyişle, bir Internet sandbox yürütülür.

.NET Framework 4'ten başlayarak, kod erişim güvenliği (CAS) ilkesi devre dışı bırakılır ve derlemeler tam güven içinde yüklenir. Normalde, bu daha önce kumlanmış olan <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> yöntemle yüklenen derlemelere tam güven verir. Bunu önlemek için, uzak bir kaynaktan yüklenen derlemelerde kod çalıştırma yeteneği varsayılan olarak devre dışı bırakılır. Varsayılan olarak, uzak bir derleme yüklemeyi <xref:System.IO.FileLoadException> denerseniz, aşağıdaki gibi bir özel durum iletisi atılır:

```text
System.IO.FileNotFoundException: Could not load file or assembly 'file:assem.dll' or one of its dependencies. Operation is not supported.
(Exception from HRESULT: 0x80131515)
File name: 'file:assem.dll' --->
System.NotSupportedException: An attempt was made to load an assembly from a network location which would have caused the assembly
to be sandboxed in previous versions of the .NET Framework. This release of the .NET Framework does not enable CAS policy by default,
so this load may be dangerous. If this load is not intended to sandbox the assembly, please enable the loadFromRemoteSources switch.
```

Derlemeyi yüklemek ve kodunu yürütmek için aşağıdakilerden birini gerçekleştirmeniz gerekir:

- Montaj için açıkça bir kum havuzu oluşturun [(bkz.](../../../misc/how-to-run-partially-trusted-code-in-a-sandbox.md)

- Derlemenin kodunu tam güven içinde çalıştırın. Bunu öğeyi `<loadFromRemoteSources>` yapılandırarak yaparsınız. .NET Framework'ün önceki sürümlerinde kısmi güven içinde çalışan derlemelerin artık .NET Framework 4 ve sonraki sürümlerde tam güven içinde çalışmasını belirtmenizi sağlar.

> [!IMPORTANT]
> Derleme tam güven içinde çalışmazise, bu yapılandırma öğesini ayarlamayın. Bunun yerine, montaj yüklemek <xref:System.AppDomain> için bir kum lu oluşturun.

Öğenin `enabled` `<loadFromRemoteSources>` özniteliği yalnızca kod erişim güvenliği (CAS) devre dışı bırakıldığında etkilidir. Varsayılan olarak, CAS ilkesi .NET Framework 4 ve sonraki sürümlerde devre dışı bırakılır. Eğer `enabled` `true`ayarlarsanız, uzak derlemeler tam güven verilir.

Ayarlanmadıysa, `enabled` aşağıdaki <xref:System.IO.FileLoadException> koşullardan biri altında a atılır: `true`

- Geçerli etki alanının kum kutulama davranışı .NET Framework 3.5'teki davranışından farklıdır. Bu, CAS ilkesinin devre dışı bırakılmasını ve geçerli etki alanının sandboxed olmamasını gerektirir.

- Yüklenen montaj `MyComputer` bölgeden değil.

Öğeyi `<loadFromRemoteSources>` bu `true` özel durum atılmasını önlemek için ayarlama. Güvenlik için yüklenen derlemeleri kumlamak için ortak dil çalışma süresine güvenmediğinizi ve bunların tam güven içinde yürütülmesine izin verilebilmesini sağlar.

## <a name="notes"></a>Notlar

- .NET Framework 4.5 ve sonraki sürümlerinde, yerel ağ hisselerindeki derlemeler varsayılan olarak tam güven içinde çalışır; öğeyi `<loadFromRemoteSources>` etkinleştirmeniz gerekmez.

- Bir uygulama web'den kopyalanmışsa, yerel bilgisayarda olsa bile Windows tarafından bir web uygulaması olarak işaretlenir. Bu atamayı dosya özelliklerini değiştirerek değiştirebilir veya `<loadFromRemoteSources>` derlemeye tam güven vermek için öğeyi kullanabilirsiniz. Alternatif olarak, işletim sisteminin <xref:System.Reflection.Assembly.UnsafeLoadFrom%2A> web'den yüklenmiş olarak işaretlediği yerel bir derlemeyi yüklemek için yöntemi kullanabilirsiniz.

- Windows Virtual <xref:System.IO.FileLoadException> PC uygulamasında çalışan bir uygulamada a alabilirsiniz. Bu, barındırma bilgisayarındaki bağlantılı klasörlerden bir dosya yüklemeyi denediğinizde olabilir. Uzak [Masaüstü Hizmetleri](/windows/win32/termserv/terminal-services-portal) (Terminal Hizmetleri) üzerinden bağlı bir klasörden dosya yüklemeyi denediğinizde de oluşabilir. Özel durum lardan `enabled` kaçınmak `true`için, '' olarak ayarlayın.

## <a name="configuration-file"></a>Yapılandırma dosyası

Bu öğe genellikle uygulama yapılandırma dosyasında kullanılır, ancak içeriğe bağlı olarak diğer yapılandırma dosyalarında kullanılabilir. Daha fazla bilgi için CAS [İlkesinin Daha Örtülü Kullanımları makalesine bakın: .NET](https://docs.microsoft.com/archive/blogs/shawnfa/more-implicit-uses-of-cas-policy-loadfromremotesources) Security blogundaki loadFromRemoteSources.  

## <a name="example"></a>Örnek

Aşağıdaki örnek, uzak kaynaklardan yüklenen derlemelere tam güvenin nasıl verilebildiğini gösterir.

```xml
<configuration>  
   <runtime>  
      <loadFromRemoteSources enabled="true"/>  
   </runtime>  
</configuration>  
```

## <a name="see-also"></a>Ayrıca bkz.

- [CAS İlkesinin Daha Örtülü Kullanımı: loadFromRemoteSources](https://docs.microsoft.com/archive/blogs/shawnfa/more-implicit-uses-of-cas-policy-loadfromremotesources)
- [Nasıl yapılır: Korumalı Alanda Kısmen Güvenilen Kodu Çalıştırma](../../../misc/how-to-run-partially-trusted-code-in-a-sandbox.md)
- [Çalışma Zamanı Ayarları Şeması](index.md)
- [Yapılandırma Dosyası Şeması](../index.md)
- <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>
