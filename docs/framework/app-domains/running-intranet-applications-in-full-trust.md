---
title: "İntranet Uygulamalarını Tam Güvende Çalıştırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- full trust, running intranet applications in
- intranet applications, running in full trust
- running intranet applications in full trust
ms.assetid: ee13c0a8-ab02-49f7-b8fb-9eab16c6c4f0
caps.latest.revision: "20"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 51a9b9ee938d6a03330d53c25fdf0468781e02a8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="running-intranet-applications-in-full-trust"></a>İntranet Uygulamalarını Tam Güvende Çalıştırma
.NET Framework sürüm 3.5 ile başlayan Service Pack 1 (SP1), uygulamaları ve bunların kitaplık derlemeleri tam güven derlemeleri olarak bir ağ paylaşımından çalıştırılabilir. <xref:System.Security.SecurityZone.MyComputer>Bölge kanıt, intranet üzerindeki paylaşımdan yüklenen derlemeler otomatik olarak eklenir. Bu bulgu aynı bilgisayarda bulunabilir derlemeleri olarak (genellikle tam güven olduğu) kümesini vermek bu derlemeler sağlar. Bu işlev ClickOnce uygulamaları veya bir ana bilgisayarda çalıştırmak için tasarlanmış uygulamalar için geçerli değildir.  
  
## <a name="rules-for-library-assemblies"></a>Kitaplık derlemeleri için kurallar  
 Bir ağ paylaşımına çalıştırılabilir tarafından yüklenen derlemeler için aşağıdaki kurallar geçerlidir:  
  
-   Kitaplık derlemeleri yürütülebilir derleme ile aynı klasörde bulunmalıdır. Bir alt klasöründe bulunan veya farklı bir yolda başvurulan derlemeleri tam güven verme kümesi verilmedi.  
  
-   Yürütülebilir dosya gecikme-bir derleme yüklerini gerekiyorsa, yürütülebilir dosya başlatmak için kullanılan aynı yol kullanmanız gerekir. Örneğin, varsa Paylaşım \\ \\ *ağ bilgisayar*\\*paylaşmak* bir sürücü harfine eşlenmez ve yürütülebilir yüklenen derlemeler bu yolundan çalıştırın Ağ yolu kullanarak yürütülebilir olarak tam güven verilecektir değil. Gecikme yükü bir derlemede için <xref:System.Security.SecurityZone.MyComputer> bölgesi, yürütülebilir dosya sürücü harfi yolu kullanmanız gerekir.  
  
## <a name="restoring-the-former-intranet-policy"></a>Eski Intranet İlkesi geri yükleniyor  
 .NET Framework önceki sürümlerinde, paylaşılan derlemeler verilmiş <xref:System.Security.SecurityZone.Intranet> bölge kanıtlar. Bir derlemeyi paylaşımında tam güven vermek için kod erişimi güvenlik ilkesi belirtin gerekiyordu.  
  
 Bu yeni davranış intranet derlemeler için varsayılandır. Sağlama önceki davranış döndürebilir <xref:System.Security.SecurityZone.Intranet> bilgisayardaki tüm uygulamalar için geçerli bir kayıt defteri anahtarını ayarlayarak kanıtlar. Bu işlem, 32 bit ve 64-bit bilgisayarlar için farklıdır:  
  
-   32-bit bilgisayarlarda HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft altında bir alt anahtar oluşturma\\. Sistem kayıt defteri anahtarında NETFramework. Anahtar adı LegacyMyComputerZone DWORD değeri 1 ile kullanın.  
  
-   64-bit bilgisayarlarda HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft altında bir alt anahtar oluşturma\\. Sistem kayıt defteri anahtarında NETFramework. Anahtar adı LegacyMyComputerZone DWORD değeri 1 ile kullanın. HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft altında aynı alt anahtarını oluşturmak\\. NETFramework anahtarı.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bütünleştirilmiş Kodlarla Programlama](../../../docs/framework/app-domains/programming-with-assemblies.md)
