---
title: <add> / <entries>
ms.date: 03/30/2017
ms.assetid: 3af4805b-dc72-4f68-b168-da4fba8c6170
ms.openlocfilehash: 23b0a825ea593f85ade870d5b93367571eaa3ec0
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850515"
---
# <a name="add-of-entries"></a>\<add> / \<entries>
Daha önce tanımlanan bir istemci uç noktasına bir filtre eşleyen bir yönlendirme girdisini temsil eder. Bu filtreyle eşleşen iletiler, bu hedefe gönderilecek.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<filterTables>**](filtertables.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<filterTable>**](filtertable.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<entries>**](entries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<routing>
  <filterTables>
    <filterTable name="String">
      <entries>
        <add backupList="String"
             endpointName="String"
             filterName="String"
             priority="Integer" />
      </entries>
    </filterTable>
  </filterTables>
</routing>
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|backupList|Uç noktaların yedekleme listesine bir başvuru belirten dize.|  
|endpoint|Özniteliği tarafından belirtilen filtreyle eşleşen iletileri alacak bir istemci uç noktası başvurusunu belirten bir dize `filterName` .|  
|Süzgeç|Bir filtre öğesine başvuruyu belirten dize.|  
|Priority|Bu girdinin önceliğini belirten bir tamsayı.<br /><br /> Yönlendirme tablosundaki girişler öncelik temelinde değerlendirilir, 0 en düşük önceliğe sahip olur. Belirli bir önceliğe yönelik tüm girişler aynı anda değerlendirilir ve geçerli öncelik için eşleşen bir giriş bulunamazsa, sonraki öncelik düzeyi değerlendirilir.<br /><br /> Bu değer isteğe bağlıdır.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<routing>](routing.md)|Yönlendirme eşleme girdilerini içeren bir yapılandırma bölümü.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement?displayProperty=nameWithType>
