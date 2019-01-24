---
title: İntranet Uygulamalarını Tam Güvende Çalıştırma
ms.date: 03/30/2017
helpviewer_keywords:
- full trust, running intranet applications in
- intranet applications, running in full trust
- running intranet applications in full trust
ms.assetid: ee13c0a8-ab02-49f7-b8fb-9eab16c6c4f0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dca1ddd1c7f13dd1ed00d06c30aa7e91acfc43ef
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54554536"
---
# <a name="running-intranet-applications-in-full-trust"></a>İntranet Uygulamalarını Tam Güvende Çalıştırma
.NET Framework sürüm 3.5 ile başlayarak Service Pack 1 (SP1), uygulamaları ve bunların kitaplık derlemeleri tam güven derlemeleri bir ağ paylaşımından çalıştırılabilir. <xref:System.Security.SecurityZone.MyComputer> Bölge kanıt, intranet üzerindeki paylaşımdan yüklenen derlemeler için otomatik olarak eklenir. Bu bulgu aynı bilgisayarda bulunabilir bütünleştirilmiş (genellikle tam güven olduğu) kümesini vermek bu derlemeler sağlar. Bu işlev, ClickOnce uygulamaları veya bir konak üzerinde çalışmak üzere tasarlanmış uygulamalar için geçerli değildir.  
  
## <a name="rules-for-library-assemblies"></a>Kitaplık derlemeleri için kuralları  
 Bir ağ paylaşımındaki bir yürütülebilir dosya tarafından yüklenen derlemeler için aşağıdaki kurallar geçerlidir:  
  
-   Kitaplık derlemeleri çalıştırılabilir derlemesinin aynı klasörde bulunmalıdır. Bir alt klasöründe bulunan veya farklı bir yolda başvurulan derlemeleri tam güven izin kümesi sunulmaz.  
  
-   Yürütülebilir dosyayı gecikme-bir derleme yükler, yürütülebilir dosyayı başlatmak için kullanılan yolu kullanmanız gerekir. Örneğin, varsa Paylaşım \\ \\ *ağ bilgisayar*\\*paylaşmak* bir sürücü harfine eşlenir ve yürütülebilir dosyayı yüklenen derlemeler bu yolundan çalıştırmak Ağ yolu kullanarak yürütülebilir olarak tam güven verilmez. Bir derlemede gecikme dışarıdan yüklemeyi <xref:System.Security.SecurityZone.MyComputer> bölgesi, yürütülebilir dosya, sürücü harfi yolu kullanmanız gerekir.  
  
## <a name="restoring-the-former-intranet-policy"></a>Eski Intranet ilke geri yükleme  
 Önceki .NET Framework sürümlerinde, paylaşılan derlemeler verilmiş <xref:System.Security.SecurityZone.Intranet> bölge kanıt. Bir paylaşımı üzerindeki bir derlemeye tam güven kazandırmak için kod erişimi güvenlik ilkesi belirtin gerekiyordu.  
  
 Bu yeni davranış intranet derlemeler için varsayılandır. Sağlama önceki davranışı geri dönebilirsiniz <xref:System.Security.SecurityZone.Intranet> bilgisayarda tüm uygulamalar için geçerli bir kayıt defteri anahtarını ayarlayarak kanıt. Bu işlem, 32-bit ve 64-bit bilgisayarlar için farklıdır:  
  
-   32-bit bilgisayarlarda HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft altında bir alt anahtar oluşturma\\. Sistem kayıt defteri anahtarında NETFramework. Anahtar adı LegacyMyComputerZone DWORD değerini 1 ile kullanın.  
  
-   64-bit bilgisayarlarda HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft altında bir alt anahtar oluşturma\\. Sistem kayıt defteri anahtarında NETFramework. Anahtar adı LegacyMyComputerZone DWORD değerini 1 ile kullanın. Aynı alt anahtarı altında HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft oluşturun\\. NETFramework anahtarı.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Bütünleştirilmiş Kodlarla Programlama](../../../docs/framework/app-domains/programming-with-assemblies.md)
