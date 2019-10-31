---
title: <loadFromRemoteSources> Öğesi
ms.date: 05/24/2018
helpviewer_keywords:
- loadFromRemoteSources element
- <loadFromRemoteSources> element
ms.assetid: 006d1280-2ac3-4db6-a984-a3d4e275046a
ms.openlocfilehash: a4dbcd0a0b848e5ef57965b5b3f4fcee9161b724
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73116559"
---
# <a name="loadfromremotesources-element"></a>\<loadFromRemoteSources > öğesi
.NET Framework 4 ve üzeri sürümlerde uzak kaynaklardan yüklenen derlemelerin tam güven verilip verilmeyeceğini belirtir.
  
> [!NOTE]
> Visual Studio proje hata listesi veya bir derleme hatası nedeniyle bu makaleye yönlendirilmiş olmanız halinde, bkz. [nasıl yapılır: Visual Studio 'Da Web 'Den derleme kullanma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ee890038(v=vs.100)).  
  
[ **\<configuration >** ](../configuration-element.md) \
&nbsp; &nbsp;[ **\<runtime >** ](runtime-element.md) \
&nbsp;&nbsp;&nbsp;&nbsp; **\<loadFromRemoteSources >**  
  
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
|`enabled`|Gerekli öznitelik.<br /><br /> Uzak bir kaynaktan yüklenen bir derlemeye tam güven verilip verilmeyeceğini belirtir.|  
  
## <a name="enabled-attribute"></a>enabled özniteliği  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`false`|Uzak kaynaklardaki uygulamalara tam güven vermeyin. Bu varsayılandır.|  
|`true`|Uzak kaynaklardaki uygulamalara tam güven verme.|  
  
### <a name="child-elements"></a>Alt öğeleri  
 Yok.  
  
### <a name="parent-elements"></a>Üst öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`runtime`|Çalışma zamanı başlatma seçenekleri hakkında bilgi içerir.|  
  
## <a name="remarks"></a>Açıklamalar

.NET Framework 3,5 ve önceki sürümlerde, uzak bir konumdan bir derlemeyi yüklerseniz, derlemedeki kod, yüklendiği bölgeye bağlı bir izin kümesiyle kısmi güvende çalışır. Örneğin, bir Web sitesinden derleme yüklerseniz Internet bölgesine yüklenir ve Internet izin kümesi verilir. Diğer bir deyişle, bir Internet korumalı alanında yürütülür.

Kod erişim güvenliği (CAS) ilkesi, .NET Framework 4 ile başlayarak devre dışıdır ve derlemeler tam güvende yüklenir. Genellikle, bu, daha önce korumalı olan <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> yöntemiyle yüklenen derlemelere tam güven verir. Bunu engellemek için, uzak bir kaynaktan yüklenen derlemelerde kod çalıştırma özelliği varsayılan olarak devre dışıdır. Varsayılan olarak, uzak bir derlemeyi yüklemeye çalışırsanız, aşağıdaki gibi bir özel durum iletisi içeren bir <xref:System.IO.FileLoadException> oluşturulur:

```text
System.IO.FileNotFoundException: Could not load file or assembly 'file:assem.dll' or one of its dependencies. Operation is not supported. 
(Exception from HRESULT: 0x80131515)
File name: 'file:assem.dll' ---> 
System.NotSupportedException: An attempt was made to load an assembly from a network location which would have caused the assembly 
to be sandboxed in previous versions of the .NET Framework. This release of the .NET Framework does not enable CAS policy by default, 
so this load may be dangerous. If this load is not intended to sandbox the assembly, please enable the loadFromRemoteSources switch. 
```

Derlemeyi yüklemek ve kodunu yürütmek için şunlardan birini yapmanız gerekir:

- Derleme için açık bir korumalı alan oluşturun (bkz. [nasıl yapılır: bir korumalı alana kısmen güvenilen kod çalıştırma](../../../misc/how-to-run-partially-trusted-code-in-a-sandbox.md)).

- Derlemenin kodunu tam güvende çalıştırın. Bunu, `<loadFromRemoteSources>` öğesini yapılandırarak yapabilirsiniz. .NET Framework önceki sürümlerinde bulunan kısmi güvende çalışan derlemelerin artık .NET Framework 4 ve sonraki sürümlerde tam güvende çalıştığını belirtmenize olanak tanır.

> [!IMPORTANT]
> Derlemenin tam güvende çalıştırılmamalıdır, bu yapılandırma öğesini ayarlamayın. Bunun yerine, derlemenin yükleneceği bir korumalı <xref:System.AppDomain> oluşturun.

`<loadFromRemoteSources>` öğesinin `enabled` özniteliği yalnızca kod erişim güvenliği (CAS) devre dışı bırakıldığında etkilidir. Varsayılan olarak, CA ilkesi .NET Framework 4 ve sonraki sürümlerde devre dışıdır. `enabled` `true`ayarlarsanız, uzak derlemelere tam güven verilir.

`enabled` `true`olarak ayarlanmamışsa, aşağıdaki koşullardan biri altında bir <xref:System.IO.FileLoadException> oluşturulur:

- Geçerli etki alanının korumalı alana alma davranışı, .NET Framework 3,5 ' deki davranışından farklıdır. Bu, CAS ilkesinin devre dışı bırakılması ve geçerli etki alanının korumalı olmaması gerekir.

- Yüklenen derleme `MyComputer` bölgesinden değil.

`<loadFromRemoteSources>` öğenin `true` ayarlanması, bu özel durumun oluşturulmasını engeller. Ortak dil çalışma zamanına bağlı olarak, güvenlik için yüklenmiş derlemeleri korumalı hale getirmenizi ve tam güvende yürütülmesine izin verilip verilmeyeceğini belirtmenizi sağlar.

## <a name="notes"></a>Notlar

- .NET Framework 4,5 ve sonraki sürümlerinde, yerel ağ paylaşımlarında derlemeler varsayılan olarak tam güvende çalışır; `<loadFromRemoteSources>` öğesini etkinleştirmeniz gerekmez.

- Bir uygulama Web 'den kopyalanmışsa, bu, yerel bilgisayarda bulunsa bile, Windows tarafından bir Web uygulaması olarak işaretlenir. Dosya özelliklerini değiştirerek bu belirtimi değiştirebilir veya derlemeye tam güven sağlamak için `<loadFromRemoteSources>` öğesini kullanabilirsiniz. Alternatif olarak, işletim sisteminin Web 'den yüklenmiş olarak işaretlediğini belirten bir yerel derlemeyi yüklemek için <xref:System.Reflection.Assembly.UnsafeLoadFrom%2A> yöntemini kullanabilirsiniz.

- Windows Sanal BILGISAYAR uygulamasında çalışan bir uygulamada <xref:System.IO.FileLoadException> alabilirsiniz. Bu, barındırma bilgisayarındaki bağlantılı klasörlerden bir dosya yüklemeye çalıştığınızda meydana gelebilir. Ayrıca, [Uzak Masaüstü Hizmetleri](https://go.microsoft.com/fwlink/?LinkId=182775) (Terminal Hizmetleri) üzerinden bağlanmış bir klasörden dosya yüklemeye çalıştığınızda da oluşabilir. Özel durumdan kaçınmak için `enabled` `true`olarak ayarlayın.

## <a name="configuration-file"></a>Yapılandırma dosyası

Bu öğe genellikle uygulama yapılandırma dosyasında kullanılır, ancak bağlama göre diğer yapılandırma dosyalarında kullanılabilir. Daha fazla bilgi için, .NET güvenlik bloguna [AIT CA 'Ların daha örtük kullanımları: loadFromRemoteSources](https://go.microsoft.com/fwlink/p/?LinkId=266839) makalesine bakın.  

## <a name="example"></a>Örnek

Aşağıdaki örnek, uzak kaynaklardan yüklenen derlemelere nasıl tam güven verildiğini gösterir.

```xml
<configuration>  
   <runtime>  
      <loadFromRemoteSources enabled="true"/>  
   </runtime>  
</configuration>  
```

## <a name="see-also"></a>Ayrıca bkz.

- [CAS Ilkesinin daha örtük kullanımları: loadFromRemoteSources](https://go.microsoft.com/fwlink/p/?LinkId=266839)
- [Nasıl yapılır: bir korumalı alanda kısmen güvenilen kod çalıştırma](../../../misc/how-to-run-partially-trusted-code-in-a-sandbox.md)
- [Çalışma Zamanı Ayarları Şeması](index.md)
- [Yapılandırma Dosyası Şeması](../index.md)
- <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>
