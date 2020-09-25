---
title: ASP.NET’te System.Transactions kullanma
description: Bir ASP.NET uygulamasının içindeki System. Transactions kullanın. Dağıtılmış işlem izinlerini etkinleştirin ve dinamik derleme ile çalışın.
ms.date: 03/30/2017
ms.assetid: 1982c300-7ea6-4242-95ed-dc28ccfacac9
ms.openlocfilehash: b6663e9258e98e94d7b739ee75c826ced1e2f897
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91186724"
---
# <a name="using-systemtransactions-in-aspnet"></a>ASP.NET’te System.Transactions kullanma

Bu konu, <xref:System.Transactions> bir ASP.NET uygulamasının içinde başarıyla nasıl kullanabileceğinizi açıklar.

## <a name="enable-distributedtransactionpermission-in-aspnet"></a>ASP.NET 'de DistributedTransactionPermission 'ı etkinleştir

 <xref:System.Transactions> kısmen güvenilen çağıranları destekler ve `AllowPartiallyTrustedCallers` özniteliğiyle işaretlenir (APTCA). Güven düzeyleri, <xref:System.Transactions> kaynak türleri (örneğin, sistem belleği, paylaşılan işlem genelinde kaynaklar, sistem genelinde kaynaklar ve diğer kaynaklar) temel alınarak tanımlanır <xref:System.Transactions> ve bu kaynaklara erişmek için gerekli olması gereken güven düzeyini kullanır. Kısmi güven ortamında, tam olmayan bir güven derlemesi yalnızca uygulama etki alanı içindeki işlemleri kullanabilir (Bu durumda, korunan tek kaynak sistem belleğidir), verilmediği müddetçe <xref:System.Transactions.DistributedTransactionPermission> .

 <xref:System.Transactions.DistributedTransactionPermission> işlem yönetiminin Microsoft Dağıtılmış İşlem Düzenleyicisi (MSDTC) tarafından yönetilmek üzere ilerletilidiğinde, talep edilir. Bu tür bir senaryo işlemi genelinde kaynakları ve MSDTC günlüğünde ayrılmış alandır özellikle bir genel kaynağı kullanır. Bir Web ön uç bir veritabanı veya veritabanı sağladığı hizmetler bir parçası olarak kullanan bir uygulama için bu kullanım örneğidir.

 ASP.NET kendi güven düzeylerine sahiptir ve ilke dosyaları aracılığıyla bu güven düzeyleriyle belirli bir izin kümesini ilişkilendirir. Daha fazla bilgi için bkz. [ASP.net Trust Levels and Policy Files](/previous-versions/aspnet/wyts434y(v=vs.100)). Windows SDK ilk yüklediğinizde, varsayılan ASP.NET ilkesi dosyalarından hiçbiri ile ilişkili değildir <xref:System.Transactions.DistributedTransactionPermission> . Bu nedenle, bir ASP.NET uygulamasındaki işlem MSDTC tarafından yönetilmek üzere ilerlediğinde, yükseltme işlemi yoğun bir şekilde başarısız olur <xref:System.Security.SecurityException> <xref:System.Transactions.DistributedTransactionPermission> . ASP.NET kısmi güven ortamında işlem yükseltmeyi etkinleştirmek için, <xref:System.Transactions.DistributedTransactionPermission> ile aynı varsayılan güven düzeylerine sahip olmanız gerekir <xref:System.Data.SqlClient.SqlClientPermission> . Bunu desteklemek için kendi özel güven düzeyinizi ve ilke dosyanızı yapılandırabilir ya da **Web_hightrust.config** ve **Web_mediumtrust.config**varsayılan ilke dosyalarını değiştirebilirsiniz.

 İlke dosyalarını değiştirmek için, öğesinin `SecurityClass` altındaki öğesine bir öğesi ekleyin `DistributedTransactionPermission` `SecurityClasses` `PolicyLevel` ve `IPermission` `NamedPermissionSet` System. Transactions için ASP.net altına karşılık gelen bir öğe ekleyin. Aşağıdaki yapılandırma dosyası bunu gösterir.

```xml
<SecurityClasses>
   <SecurityClass Name="DistributedTransactionPermission" Description="System.Transactions.DistributedTransactionPermission, System.Transactions, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"/>
...
</SecurityClasses>

<PermissionSet
  class="NamedPermissionSet"
  version="1"
  Name="ASP.Net">
     <IPermission
        class="System.Transactions.DistributedTransactionPermission, System.Transactions, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
        version="1"
        Unrestricted="true"
     />
...
</PermissionSet>
```

 ASP.NET güvenlik ilkesi hakkında daha fazla bilgi için bkz. [SecurityPolicy öğesi (ASP.NET Settings şeması)](/previous-versions/dotnet/netframework-4.0/zhs35b56(v=vs.100)).

## <a name="dynamic-compilation"></a>Dinamik derleme

 <xref:System.Transactions>Erişim için dinamik olarak derlenen bir ASP.NET uygulamasında içeri ve kullanmak istiyorsanız, yapılandırma dosyasındaki derlemeye bir başvuru yerleştirmeniz gerekir <xref:System.Transactions> . Özel olarak, başvuru `compilation/assemblies` varsayılan kök **Web.config** yapılandırma dosyasının bölümünün altına veya belirli bir Web uygulamasının yapılandırma dosyasına eklenmelidir. Aşağıdaki örnek bunu gösterir.

```xml
<configuration>
   <system.web>
      <compilation>
         <assemblies>
      <add assembly="System.Transactions, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />
         </assemblies>
      </compilation>
   </system.web>
</configuration>
```

 Daha fazla bilgi için bkz. [derleme için derlemeler Için öğe ekleme (ASP.NET Settings şeması)](/previous-versions/dotnet/netframework-4.0/37e2zyhb(v=vs.100)).

## <a name="see-also"></a>Ayrıca bkz.

- [ASP.NET güven düzeyleri ve Ilke dosyaları](/previous-versions/aspnet/wyts434y(v=vs.100))
- [securityPolicy öğesi (ASP.NET Settings şeması)](/previous-versions/dotnet/netframework-4.0/zhs35b56(v=vs.100))
- [İşlem Yönetimi Yükseltme](transaction-management-escalation.md)
