---
title: <loadFromRemoteSources> Öğesi
ms.date: 05/24/2018
helpviewer_keywords:
- loadFromRemoteSources element
- <loadFromRemoteSources> element
ms.assetid: 006d1280-2ac3-4db6-a984-a3d4e275046a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7568129f30267b212737ec8aa688cf882e19bbff
ms.sourcegitcommit: b8ace47d839f943f785b89e2fff8092b0bf8f565
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2019
ms.locfileid: "55675315"
---
# <a name="loadfromremotesources-element"></a>\<loadFromRemoteSources > öğesi
Uzak kaynaklardan yüklenen derlemeler .NET Framework 4 ve daha sonra tam güven izni olup olmadığını belirtir.
  
> [!NOTE]
>  Bu makalede, bir hata iletisi Visual Studio projesi hata listesi veya bir yapı hatası nedeniyle yönlendirildiniz olup [nasıl yapılır: Visual Studio'da bir bütünleştirilmiş kod Web'den kullanmak](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ee890038(v=vs.100)).  
  
 \<Yapılandırma >  
\<çalışma zamanı >  
\<loadFromRemoteSources >  
  
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
|`enabled`|Gerekli öznitelik.<br /><br /> Bir uzak kaynaktan yüklenen bir derlemeyi tam güven izni olup olmadığını belirtir.|  
  
## <a name="enabled-attribute"></a>Etkin öznitelik  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`false`|Tam güven uzak kaynaklardan gelen uygulamalara vermeyin. Bu varsayılandır.|  
|`true`|Tam güven uzak kaynaklardan gelen uygulamalara verin.|  
  
### <a name="child-elements"></a>Alt öğeleri  
 Yok.  
  
### <a name="parent-elements"></a>Üst öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`runtime`|Çalışma zamanı başlatma seçenekleri hakkında bilgi içerir.|  
  
## <a name="remarks"></a>Açıklamalar

Uzak bir konumdan bir derlemeyi yüklemek, .NET Framework 3.5 ve önceki sürümlerinde derleme içindeki kod kısmi güven, yüklendiği bölgesine bağlıdır bir izin kümesi ile çalışır. Örneğin, bir Web sitesinden bir derlemeyi yüklemek, bu Internet bölgesine yüklendi ve Internet izni verildi. Diğer bir deyişle, bir Internet korumalı alan içinde yürütülür.

.NET Framework 4 ile başlayarak, kod erişimi güvenliği (CAS) ilkesi devre dışı bırakıldı ve derlemeleri tam güven yüklenir. Normalde, bu tam güven ile yüklenen derlemeler vermek <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> önceden korumalı olan yöntem. Bunu önlemek için bir uzak kaynaktan yüklü bütünleştirilmiş kodu çalıştırma olanağı varsayılan olarak devre dışıdır. Varsayılan olarak uzak bir derlemeyi yüklemeye çalışırsanız, bir <xref:System.IO.FileLoadException> ile aşağıdaki durum gibi bir özel durum iletisi:

```text
System.IO.FileNotFoundException: Could not load file or assembly 'file:assem.dll' or one of its dependencies. Operation is not supported. 
(Exception from HRESULT: 0x80131515)
File name: 'file:assem.dll' ---> 
System.NotSupportedException: An attempt was made to load an assembly from a network location which would have caused the assembly 
to be sandboxed in previous versions of the .NET Framework. This release of the .NET Framework does not enable CAS policy by default, 
so this load may be dangerous. If this load is not intended to sandbox the assembly, please enable the loadFromRemoteSources switch. 
```

Derlemeyi yüklemek ve kendi kod yürütmek için aşağıdakilerden birini yapmanız gerekir:

- Açıkça bir korumalı alan için derleme oluşturma (bkz [nasıl yapılır: Korumalı alanda kısmen güvenilen kodu çalıştırma](../../../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md)).

- Derlemenin kod tam güvende çalıştırma. Yapılandırarak bunu `<loadFromRemoteSources>` öğesi. .NET Framework'ün önceki sürümlerindeki kısmi güvende çalışan derlemeler artık .NET Framework 4 ve sonraki sürümlerde tam güven içinde çalıştığını belirtmenize olanak tanır.

> [!IMPORTANT]
> Bütünleştirilmiş kod tam güvende çalıştırılmayacaksa, bu yapılandırma öğesi ayarlamayın. Bunun yerine, bir korumalı alan oluşturma <xref:System.AppDomain> hangi derlemesi yüklenemiyor.

`enabled` Özniteliğini `<loadFromRemoteSources>` öğedir etkili yalnızca zaman kod erişimi güvenliği (CAS) devre dışı bırakılır. Varsayılan olarak, .NET Framework 4 ve sonraki sürümlerinde, CAS ilkesini devre dışıdır. Ayarlarsanız `enabled` için `true`, uzak derlemeleri tam güven izni.

Varsa `enabled` ayarlı değil `true`, <xref:System.IO.FileLoadException> aşağıdaki durumlardan herhangi biri altında oluşturulur:

- Geçerli etki alanı korumalı alana alma davranışını, .NET Framework 3.5, davranışı farklıdır. Bu, CAS ilkesini devre dışı bırakılması ve korumalı olmaması için geçerli etki alanı gerektirir.

- Yüklenen derleme gelen değil `MyComputer` bölge.

Ayarı `<loadFromRemoteSources>` öğesine `true` öğesinden oluşturulan bu özel durumu önler. Ortak dil çalışma zamanı için korumalı alan yüklenen derlemeler için güvenlik bağlı değil, belirtmenizi sağlar ve bunlar içinde yürütülen olmasına izin, tam güven.

## <a name="notes"></a>Notlar

- .NET Framework 4.5 ve sonraki sürümlerinde, yerel ağ paylaşımlarında derlemeleri tam güven varsayılan olarak çalıştırın; etkinleştirme gerekmez `<loadFromRemoteSources>` öğesi.

- Bir uygulamanın Web'den kopyalandı, yerel bilgisayarda bulunsa bile, Windows tarafından bir web uygulaması olacak şekilde işaretlenir. Dosya özelliklerini değiştirerek bu ataması değiştirebilir veya kullanabileceğiniz `<loadFromRemoteSources>` öğesi derlemeyi vermek için tam güven. Alternatif olarak, kullandığınız <xref:System.Reflection.Assembly.UnsafeLoadFrom%2A> yöntemi işletim sistemi Web'den yüklenmiş olan olarak işaretlenmiş bir yerel derlemesi yüklenemiyor.

- Alabilirsiniz bir <xref:System.IO.FileLoadException> bir Windows Virtual PC uygulama içinde çalışan bir uygulamada. Bağlantılı klasörlerden barındıran bilgisayarda bir dosya yüklemeye çalıştığınızda bu durum oluşabilir. Ayrıca üzerinden bağlı bir klasörden bir dosya yüklemeye çalıştığınızda oluşabilir [Uzak Masaüstü Hizmetleri](https://go.microsoft.com/fwlink/?LinkId=182775) (Terminal Hizmetleri). Özel durumdan kaçınmak için ayarlanmış `enabled` için `true`.

## <a name="configuration-file"></a>Yapılandırma dosyası

Bu öğe uygulama yapılandırma dosyasında genellikle kullanılır, ancak diğer yapılandırma dosyalarını bağlam bağlı olarak kullanılabilir. Daha fazla bilgi için bkz [daha fazla örtük kullanır, CAS ilkesini: loadFromRemoteSources](https://go.microsoft.com/fwlink/p/?LinkId=266839) .NET güvenliği blogundaki.  

## <a name="example"></a>Örnek

Aşağıdaki örnek, uzak kaynaklardan yüklenen derlemeleri tam güven vermek gösterilmektedir.

```xml
<configuration>  
   <runtime>  
      <loadFromRemoteSources enabled="true"/>  
   </runtime>  
</configuration>  
```

## <a name="see-also"></a>Ayrıca bkz.

- [CAS ilkesini daha örtük kullanır: loadFromRemoteSources](https://go.microsoft.com/fwlink/p/?LinkId=266839)
- [Nasıl yapılır: Korumalı alanda kısmen güvenilen kodu çalıştırma](../../../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md)
- [Çalışma Zamanı Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Yapılandırma Dosyası Şeması](../../../../../docs/framework/configure-apps/file-schema/index.md)
- <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>
