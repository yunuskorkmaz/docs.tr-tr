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
ms.openlocfilehash: 012c2e70e66015bc317606a7eea07812b5df26e7
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91183929"
---
# <a name="throwunobservedtaskexceptions-element"></a>\<ThrowUnobservedTaskExceptions> Öğesi

İşlenmemiş görev özel durumlarının çalışan bir işlemi sonlandırmayı gerekip gerekmediğini belirtir.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<ThrowUnobservedTaskExceptions>**  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<ThrowUnobservedTaskExceptions  
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  

 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`enabled`|Gerekli öznitelik.<br /><br /> İşlenmemiş görev özel durumlarının çalışan işlemi sonlandırmayı gerekip gerekmediğini belirtir.|  
  
## <a name="enabled-attribute"></a>etkin Öznitelik  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`false`|İşlenmemiş bir görev özel durumu için çalışan işlemi sonlandırır. Bu varsayılan seçenektir.|  
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

 İle ilişkili bir özel durum <xref:System.Threading.Tasks.Task> gözlemlenmeyen bir <xref:System.Threading.Tasks.Task.Wait%2A> işlem yok, üst öğe iliştirilmemiş ve <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> özellik okunamadı, görev özel durumu gözlemlenmemiş olarak kabul edilir.  
  
 .NET Framework 4 ' te, varsayılan olarak, gözlemlenen olmayan bir <xref:System.Threading.Tasks.Task> özel durum atık olarak toplanmışsa Sonlandırıcı bir özel durum oluşturur ve işlemi sonlandırır. İşlemin sonlandırılması çöp toplama ve sonlandırma zamanlaması tarafından belirlenir.  
  
 Geliştiricilerin görevlere göre zaman uyumsuz kod yazmasını kolaylaştırmak için .NET Framework 4,5, gözlemlenen özel durumlar için bu varsayılan davranışı değiştirir. Gözlemlenen özel durumlar hala etkinliğin oluşturulmasına neden olur <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException> , ancak varsayılan olarak işlem sonlanmaz. Bunun yerine, bir olay işleyicisinin özel durumu görmediğine bakılmaksızın, olay oluşturulduktan sonra özel durum yoksayılır.  
  
 .NET Framework 4,5 ' de, bir özel durum oluşturan .NET Framework 4 davranışını etkinleştirmek için bir uygulama yapılandırma dosyasındaki [ \<ThrowUnobservedTaskExceptions> öğesini](throwunobservedtaskexceptions-element.md) kullanabilirsiniz.  
  
 Özel durum davranışını aşağıdaki yollarla da belirtebilirsiniz:  
  
- Ortam değişkenini `COMPlus_ThrowUnobservedTaskExceptions` ( `set COMPlus_ThrowUnobservedTaskExceptions=1` ) ayarlayarak.  
  
- ThrowUnobservedTaskExceptions = 1 kayıt defteri DWORD değerini HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft olarak ayarlayarak \\ . NETFramework anahtarı.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, bir uygulama yapılandırma dosyası kullanarak görevlerde özel durumların üretilmesini nasıl etkinleştireceğinizi gösterir.  
  
```xml  
<configuration>
    <runtime>
        <ThrowUnobservedTaskExceptions enabled="true"/>
    </runtime>
</configuration>  
```  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnekte, bir görevden gözlemlenen bir özel durumun nasıl oluşturulduğu gösterilmektedir. Kod, doğru bir şekilde çalışması için yayınlanmış bir program olarak çalıştırılmalıdır.  
  
 [!code-csharp[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/throwunobservedtaskexceptions/cs/program.cs#1)]
 [!code-vb[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/throwunobservedtaskexceptions/vb/program.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma zamanı ayarları şeması](index.md)
- [Yapılandırma dosyası şeması](../index.md)
