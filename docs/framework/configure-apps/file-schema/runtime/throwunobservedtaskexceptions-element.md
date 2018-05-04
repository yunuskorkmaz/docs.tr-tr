---
title: '&lt;ThrowUnobservedTaskExceptions&gt; öğesi'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ThrowUnobservedTaskExceptions element
- <ThrowUnobservedTaskExceptions> element
ms.assetid: cea7e588-8b8d-48d2-9ad5-8feaf3642c18
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3f72bedbaaf0b15ade7ff6b7b8c3edcdfd3fda6d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltthrowunobservedtaskexceptionsgt-element"></a>&lt;ThrowUnobservedTaskExceptions&gt; öğesi
İşlenmemiş görev özel durumlarını çalışan bir işlemi sonlandırmak olup olmadığını belirtir.  
  
 \<Yapılandırma >  
\<çalışma zamanı >  
\<ThrowUnobservedTaskExceptions >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<ThrowUnobservedTaskExceptions  
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`enabled`|Gerekli öznitelik.<br /><br /> İşlenmemiş görev özel durumlarını çalışan işlemi sonlanmalıdır olup olmadığını belirtir.|  
  
## <a name="enabled-attribute"></a>etkin Öznitelik  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`false`|Bir görev işlenmeyen özel durum için çalışan işlemi sonlandırmak değil. Bu varsayılandır.|  
|`true`|Bir görev işlenmeyen özel durum için çalışan işlemi sonlandırır.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`runtime`|Çalışma zamanı başlatma seçenekleri hakkında bilgi içerir.|  
|||  
  
## <a name="remarks"></a>Açıklamalar  
 İle ilişkili bir özel durum, bir <xref:System.Threading.Tasks.Task> olmayan gözlenir, var. hiçbir <xref:System.Threading.Tasks.Task.Wait%2A> işlemi, üst iliştirilmemiş ve <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> özelliği, görev özel durum olarak kabul unobserved olması değil okundu.  
  
 İçinde [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], göre varsayılan bir <xref:System.Threading.Tasks.Task> bir unobserved olan özel durum çöp toplama, sonlandırıcıyı bir özel durum oluşturur ve işlemi sonlandırır. İşlem sonlandırma çöp toplama ve sonlandırma zamanlama tarafından belirlenir.  
  
 Geliştiriciler görevlerini temel alan zaman uyumsuz kod yazmayı kolaylaştırmak için [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)] unobserved özel durumlar için bu varsayılan davranışı değiştirir. Özel durumlar hala neden unobserved <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException> oluşturulması için olay ancak varsayılan olarak, işlem değil sonlandırılacak. Bunun yerine, bir olay işleyicisi özel gözlemleyen bağımsız olarak olay tetiklenir sonra özel durum göz ardı edilir.  
  
 İçinde [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)], kullanabileceğiniz [ \<ThrowUnobservedTaskExceptions > öğesi](../../../../../docs/framework/configure-apps/file-schema/runtime/throwunobservedtaskexceptions-element.md) etkinleştirmek için bir uygulama yapılandırma dosyasında [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] bir özel durum atma davranışı.  
  
 Ayrıca aşağıdaki yollardan biriyle özel durum davranışını belirtebilirsiniz:  
  
-   Ortam değişkenini ayarlayarak `COMPlus_ThrowUnobservedTaskExceptions` (`set COMPlus_ThrowUnobservedTaskExceptions=1`).  
  
-   DWORD kayıt defteri ayarı ThrowUnobservedTaskExceptions değer = 1 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. NETFramework anahtarı.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, görevleri özel durumları atma uygulama yapılandırma dosyası kullanarak etkinleştirmek gösterilmiştir.  
  
```xml  
<configuration>   
    <runtime>   
        <ThrowUnobservedTaskExceptions enabled="true"/>   
    </runtime>   
</configuration>  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir unobserved özel bir görevden nasıl durum gösterir. Kod düzgün çalışması için yayımlanan bir program olarak çalıştırmanız gerekir.  
  
 [!code-csharp[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/throwunobservedtaskexceptions/cs/program.cs#1)]
 [!code-vb[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/throwunobservedtaskexceptions/vb/program.vb#1)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çalışma Zamanı Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Yapılandırma Dosyası Şeması](../../../../../docs/framework/configure-apps/file-schema/index.md)
