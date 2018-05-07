---
title: Oracle için .NET Framework veri sağlayıcısı için sistem gereksinimleri
ms.date: 03/30/2017
ms.assetid: 054f76b9-1737-43f0-8160-84a00a387217
ms.openlocfilehash: a5ce0e831af40cbe86e6ac901d6e92d5a60f8774
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="system-requirements-for-the-net-framework-data-provider-for-oracle"></a>Oracle için .NET Framework veri sağlayıcısı için sistem gereksinimleri
Oracle için .NET Framework veri sağlayıcısı Microsoft Data Access Components (MDAC) 2.6 veya sonraki sürümünü gerektirir. MDAC 2.8 SP1 önerilir.  
  
 Oracle 8i sürüm 3 (8.1.7) istemcisi de sahip olmalıdır veya sonraki bir sürümü yüklü.  
  
 UTF16 Oracle 9i yeni bir özellik olduğundan oracle istemci yazılımı sürümü Oracle 9i önce UTF16 veritabanlarına erişemez. Bu özelliği kullanmak için istemci yazılımını Oracle 9i veya sonraki bir sürüme yükseltmeniz gerekir.  
  
## <a name="working-with-the-data-provider-for-oracle-and-unicode-data"></a>Oracle ve Unicode verileri için veri sağlayıcı ile çalışma  
 .NET Framework Veri Sağlayıcısı ile istemci kitaplıkları Oracle ve Oracle için çalışırken düşünmelisiniz Unicode ilgili sorunların bir listesi verilmiştir. Daha fazla bilgi için Oracle belgelerinize bakın.  
  
### <a name="setting-the-unicode-value-in-a-connection-string-attribute"></a>Bir bağlantı dizesi özniteliği Unicode değerini ayarlama  
 Oracle ile çalışırken, bağlantı dizesi özniteliği kullanabilirsiniz  
  
```  
Unicode=True   
```  
  
 Oracle istemci kitaplıkları UTF-16 modunda başlatılamadı. Bu, kitaplıkları (olan UCS-2'ye çok benzer) UTF-16 çok baytlı dizeleri yerine kabul etmek Oracle istemcisi neden olur. Bu her zaman ek çeviri iş olmadan herhangi bir Oracle kod sayfasında çalışmak Oracle için veri sağlayıcı sağlar. Bu yapılandırma, yalnızca AL16UTF16 alternatif karakter kümesini içeren bir Oracle 9i veritabanıyla iletişim kurmak için Oracle 9i istemcileri kullanıyorsanız çalışır. Bir Oracle 9i istemcisi bir Oracle 9i sunucusuyla iletişim kurduğunda, ek kaynaklar Unicode dönüştürme için gerekli **CommandText** uygun çok baytlı karakter değerlere ayarlayın, Oracle9i sunucusu kullanır. Güvenli yapılandırma ekleyerek olduğunu bildiğiniz durumlarda bu önlenebilir `Unicode=True` , bağlantı dizesi.  
  
### <a name="mixing-versions-of-oracle-client-and-oracle-server"></a>Oracle istemcisi ve Oracle Server sürümleri karıştırma  
 Oracle 8i istemcileri erişemiyor **NCHAR**, **NVARCHAR2**, veya **NCLOB** sunucunun Ulusal karakter kümesi AL16UTF16 belirtildiğinde Oracle 9i veritabanlarındaki veriler ( Oracle 9i için varsayılan ayar). Çünkü UTF-16 karakter kümesi 8i istemciler bunu okuyamıyor Oracle Oracle 9i kadar sunulan değil desteği.  
  
### <a name="working-with-utf-8-data"></a>UTF-8 verileri ile çalışma  
 Alternatif karakter kümesini ayarlamak için kayıt defteri anahtarı HKEY_LOCAL_MACHINE\SOFTWARE\ORACLE\HOMEID\NLS_LANG UTF8 için ayarlayın. Daha fazla bilgi için bir platformda Oracle yükleme notlarına bakın. Varsayılan ayar, Oracle istemci yazılımını yüklediğiniz dil birincil karakter kümesidir. Bağlanmakta olduğunuz veritabanı Ulusal dil karakter kümesi ile eşleşmesi için dil ayarı bulunamadı, verileri, birincil veritabanı karakter kümesinde, Ulusal karakter kümesi gönderip parametre ve sütun bağlamaları neden olur.  
  
### <a name="oraclelob-can-only-update-full-characters"></a>OracleLob Can yalnızca tam karakter güncelleştirin.  
 Kullanılabilirlik nedenlerle <xref:System.Data.OracleClient.OracleLob> nesnesi .NET Framework akış sınıfından devralan ve sağlar **ReadByte** ve **WriteByte** yöntemleri. Bunu ayrıca yöntemleri gibi uygulayan **CopyTo** ve **silme**, bu iş Oracle bölümlerde **LOB** nesneleri. Buna karşılık, Oracle istemci yazılımını bir karakteri ile çalışmak için API'ler sağlar **LOB**s (**CLOB** ve **NCLOB**). Ancak, bu API'leri yalnızca tam karakterler üzerinde çalışır. Bu farklılık nedeniyle, Oracle veri sağlayıcısı için destek uygular **okuma** ve **ReadByte** byte-wise bir biçimde UTF-16 verilerle çalışmak için. Ancak, diğer yöntemleri **OracleLob** nesne yalnızca tam karakter işlemleri izin verin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Oracle ve ADO.NET](../../../../docs/framework/data/adonet/oracle-and-adonet.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
