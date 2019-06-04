---
title: <ThrowUnobservedTaskExceptions> Öğesi
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
ms.openlocfilehash: 9647297bf976d26a97be0da8807d607789e8a065
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66489580"
---
# <a name="throwunobservedtaskexceptions-element"></a>\<ThrowUnobservedTaskExceptions > öğesi
Çalışan bir işleme, işlenmemiş bir görev özel durumlarını sonlandırma olup olmadığını belirtir.  
  
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
|`enabled`|Gerekli öznitelik.<br /><br /> İşlenmemiş bir görev özel durumlarını çalışan işlemi sonlandırması gerektiğini belirtir.|  
  
## <a name="enabled-attribute"></a>etkin Öznitelik  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`false`|İşlenmemiş bir görev özel durum için çalışan işlemi sonlandırmak değil. Bu varsayılandır.|  
|`true`|İşlenmemiş bir görev özel durum için çalışan işlemi sonlandırır.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`runtime`|Çalışma zamanı başlatma seçenekleri hakkında bilgi içerir.|  
|||  
  
## <a name="remarks"></a>Açıklamalar  
 İle ilişkili bir özel durum, bir <xref:System.Threading.Tasks.Task> gözlenmezse, orada hiçbir <xref:System.Threading.Tasks.Task.Wait%2A> işlemi, üst iliştirilmemiş ve <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> özelliği olmayan salt okunur görev özel durum gözetimsiz olarak kabul edilir.  
  
 Varsayılan olarak, .NET Framework 4'te, bir <xref:System.Threading.Tasks.Task> gözetimsiz bir olan özel durum çöp olarak toplanacak, sonlandırıcı bir özel durum oluşturur ve işlemi sonlandırır. İşlemin sonlandırılmasına atık toplama ve sonlandırma zamanlaması tarafından belirlenir.  
  
 Geliştiriciler görevlerini temel alan zaman uyumsuz kod yazmayı kolaylaştırmak için .NET Framework 4.5 gözetimsiz özel durumlar için bu varsayılan davranışı değiştirir. Gözlemlenmeyen özel durumlar hala neden <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException> oluşturulması için olay ancak varsayılan olarak, işlem değil sonlandırın. Bunun yerine, özel durum gözlemler bağımsız olarak bir olay işleyicisi, olay tetiklenir sonra özel durum yok sayılır.  
  
 .NET Framework 4.5, kullandığınız [ \<ThrowUnobservedTaskExceptions > öğesi](../../../../../docs/framework/configure-apps/file-schema/runtime/throwunobservedtaskexceptions-element.md) bir özel durum .NET Framework 4 davranışını etkinleştirmek için bir uygulama yapılandırma dosyasında.  
  
 Özel durum davranışını aşağıdaki yollardan birini belirtebilirsiniz:  
  
- Ortam değişkenini ayarlayarak `COMPlus_ThrowUnobservedTaskExceptions` (`set COMPlus_ThrowUnobservedTaskExceptions=1`).  
  
- DWORD kayıt defteri ayarı ThrowUnobservedTaskExceptions değer = 1 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. NETFramework anahtarı.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, görevlerde özel durumları atma bir uygulama yapılandırma dosyası kullanarak etkinleştirmek gösterilmektedir.  
  
```xml  
<configuration>   
    <runtime>   
        <ThrowUnobservedTaskExceptions enabled="true"/>   
    </runtime>   
</configuration>  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek nasıl gözetimsiz bir görevden özel durum gösterir. Kodun düzgün çalışması için yayımlanmış bir program olarak çalıştırmanız gerekir.  
  
 [!code-csharp[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/throwunobservedtaskexceptions/cs/program.cs#1)]
 [!code-vb[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/throwunobservedtaskexceptions/vb/program.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma Zamanı Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Yapılandırma Dosyası Şeması](../../../../../docs/framework/configure-apps/file-schema/index.md)
