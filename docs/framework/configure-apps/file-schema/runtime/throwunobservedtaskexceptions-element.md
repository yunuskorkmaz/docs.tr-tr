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
ms.openlocfilehash: de5a686bcbd88fc52173b488103f033575623d62
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153821"
---
# <a name="throwunobservedtaskexceptions-element"></a>\<ThrowUnobservedTaskExceptions> Öğesi
İşlenmemiş görev özel durumlarının çalışan bir işlemi sonlandırıp sonlandırmayacağını belirtir.  
  
[**\<yapılandırma>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<çalışma zamanı>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<ThrowUnobservedTaskExceptions>**  
  
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
|`enabled`|Gerekli öznitelik.<br /><br /> İşlenmemiş görev özel durumlarının yürütme işlemini sonlandırıp sonlandırmayacağını belirtir.|  
  
## <a name="enabled-attribute"></a>etkin Öznitelik  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`false`|İşlenmemiş bir görev özel durumu için çalışan işlemi sonlandırmaz. Bu varsayılandır.|  
|`true`|İşlenmemiş bir görev özel durumu için çalışan işlemi sonlandırır.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`runtime`|Çalışma zamanı başlatma seçenekleri hakkında bilgi içerir.|  
|||  
  
## <a name="remarks"></a>Açıklamalar  
 Bir <xref:System.Threading.Tasks.Task> özel durumla ilişkili bir özel durum gözlenmemişse, işlem yapılmaz, <xref:System.Threading.Tasks.Task.Wait%2A> üst <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> öğe eklenmez ve özellik okunmamışsa görev özel durumu gözlenmemiş olarak kabul edilir.  
  
 .NET Framework 4'te, varsayılan <xref:System.Threading.Tasks.Task> olarak, gözlenmeyen bir özel durum varsa, çöp toplanmışsa, sonlandırıcı bir özel durum atar ve işlemi sonlandırır. Sürecin sona ermesi çöp toplama ve sonuçlandırma zamanlaması ile belirlenir.  
  
 Geliştiricilerin görevlere dayalı eşzamanlı kod yazmasını kolaylaştırmak için .NET Framework 4.5 bu varsayılan davranışı gözlenmemiş özel durumlar için değiştirir. Gözlenmeyen özel durumlar <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException> yine de olayın yükseltilmesine neden olur, ancak varsayılan olarak işlem sonlandırmaz. Bunun yerine, olay büyütüldükten sonra, bir olay işleyicisinin özel durumu gözlemleyip izlemediğine bakılmaksızın özel durum yoksayılır.  
  
 .NET Framework 4.5'te, bir uygulama yapılandırma dosyasındaki [ \<ThrowUnobservedTaskExceptions> öğesini](throwunobservedtaskexceptions-element.md) kullanarak .NET Framework 4'ün özel durum atma davranışını etkinleştirebilirsiniz.  
  
 Özel durum davranışını aşağıdaki yollardan birinde de belirtebilirsiniz:  
  
- Çevre değişkenini `COMPlus_ThrowUnobservedTaskExceptions` `set COMPlus_ThrowUnobservedTaskExceptions=1`ayarlayarak ( ).  
  
- Kayıt defteri DWORD değeri ThrowUnobservedTaskExceptions = 1 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\ayarlayarak . NETFramework anahtarı.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, bir uygulama yapılandırma dosyası kullanarak görevlerde özel durumların atılması nasıl etkinleştirilir gösterilmektedir.  
  
```xml  
<configuration>
    <runtime>
        <ThrowUnobservedTaskExceptions enabled="true"/>
    </runtime>
</configuration>  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, gözlenmeyen bir özel durum bir görevden nasıl atıldığını gösterir. Kodun düzgün çalışması için serbest bırakılmış bir program olarak çalıştırılması gerekir.  
  
 [!code-csharp[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/throwunobservedtaskexceptions/cs/program.cs#1)]
 [!code-vb[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/throwunobservedtaskexceptions/vb/program.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma Zamanı Ayarları Şeması](index.md)
- [Yapılandırma Dosyası Şeması](../index.md)
