---
title: Oracle için .NET Framework veri sağlayıcısı için sistem gereksinimleri
ms.date: 03/30/2017
ms.assetid: 054f76b9-1737-43f0-8160-84a00a387217
ms.openlocfilehash: cc3fc61c5adebf67b1203897579b2f959cbc0546
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54670886"
---
# <a name="system-requirements-for-the-net-framework-data-provider-for-oracle"></a>Oracle için .NET Framework veri sağlayıcısı için sistem gereksinimleri
Oracle için .NET Framework veri sağlayıcısı, Microsoft Data Access Components (MDAC) 2.6 veya sonraki sürümünü gerektirir. MDAC 2.8 SP1 önerilir.  
  
 Sonraki bir sürümünün yüklü veya Oracle 8i sürüm 3 (8.1.7) istemcisini de olmalıdır.  
  
 UTF16 Oracle 9i yeni bir özellik olduğundan, oracle istemci yazılımı sürümünden Oracle 9i UTF16 veritabanlarına erişemez. Bu özelliği kullanmak için istemci yazılımını Oracle 9i veya sonraki bir sürüme yükseltmeniz gerekir.  
  
## <a name="working-with-the-data-provider-for-oracle-and-unicode-data"></a>Oracle ve Unicode verileri için veri sağlayıcısı ile çalışma  
 İstemci kitaplıkları Oracle ve Oracle için .NET Framework Veri Sağlayıcısı ile çalışırken göz önünde bulundurmanız gereken Unicode ilgili sorunların bir listesini aşağıda verilmiştir. Daha fazla bilgi için Oracle belgelerinize bakın.  
  
### <a name="setting-the-unicode-value-in-a-connection-string-attribute"></a>Bir bağlantı dizesi özniteliği Unicode değerini ayarlama  
 Oracle ile çalışırken, bağlantı dizesi özniteliği kullanabilirsiniz.  
  
```  
Unicode=True   
```  
  
 UTF-16 modunda Oracle istemci kitaplıkları başlatılamadı. Bu kitaplıklar (olan UCS-2'ye çok benzer) UTF-16 çok baytlı dizeleri yerine kabul etmek Oracle istemcisini neden olur. Bu çeviri ek çalışma yapmadan herhangi bir Oracle kod sayfasında her zaman çalışmak Oracle veri sağlayıcısı sağlar. Bir Oracle 9i AL16UTF16 diğer karakter kümesini veritabanıyla iletişim kurmak için Oracle 9i istemcileri kullanıyorsanız bu yapılandırma yalnızca çalışır. Bir Oracle 9i istemci bir Oracle 9i sunucusuyla iletişim kurduğunda, Unicode dönüştürmek için ek kaynaklar gereklidir **CommandText** uygun çok baytlı karakter değerlere ayarlayın, Oracle9i sunucusu kullanır. Güvenli yapılandırma ekleyerek olduğunu bildiğiniz durumlarda bu önlenebilir `Unicode=True` , bağlantı dizesi.  
  
### <a name="mixing-versions-of-oracle-client-and-oracle-server"></a>Oracle istemci ve Oracle Server sürümlerini karıştırma  
 Oracle 8i istemciler erişemiyor **NCHAR**, **NVARCHAR2**, veya **NCLOB** sunucunun Ulusal karakter kümesi AL16UTF16 belirtildiğinde Oracle 9i veritabanlarındaki verileri ( Oracle 9i için varsayılan ayar). Çünkü UTF-16 karakter kümesi 8i istemciler, okuyamıyor Oracle Oracle 9i kadar tanıtıldı desteği.  
  
### <a name="working-with-utf-8-data"></a>UTF-8 verilerle çalışma  
 Diğer karakter kümesini ayarlamak için kayıt defteri anahtarı HKEY_LOCAL_MACHINE\SOFTWARE\ORACLE\HOMEID\NLS_LANG UTF8 için ayarlayın. Oracle yükleme notları platformunuz daha fazla bilgi için bkz. Oracle istemci yazılımı yüklemekte olduğunuz dil birincil karakter kümesi varsayılan ayardır. Bağlanmakta olduğunuz veritabanı Ulusal dil karakter kümesiyle eşleşen dil ayarları göndermek veya veri, birincil veritabanı karakter kümesinde olmayan Ulusal karakter kümesini almak parametre ve sütun bağlamaları neden olur.  
  
### <a name="oraclelob-can-only-update-full-characters"></a>OracleLob Can yalnızca tam karakter güncelleştirin.  
 Kullanılabilirlik nedenlerinden dolayı için <xref:System.Data.OracleClient.OracleLob> nesne .NET Framework Stream sınıfından devralır ve sağlar **ReadByte** ve **WriteByte** yöntemleri. Ayrıca yöntemler gibi uygular **CopyTo** ve **silme**, bu bölümlerde Oracle iş **LOB** nesneleri. Buna karşılık, Oracle istemci yazılımı karakteri ile çalışmak için API'ler sunar **LOB**s (**CLOB** ve **NCLOB**). Ancak, bu API'leri yalnızca tam karakterler üzerinde çalışır. Bu farklılık nedeniyle, Oracle için veri sağlayıcısı için destek uygular **okuma** ve **ReadByte** byte-wise bir şekilde UTF-16 verilerle çalışmak için. Ancak, diğer yöntemleri **OracleLob** nesne yalnızca tam karakter operations izin verin.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Oracle ve ADO.NET](../../../../docs/framework/data/adonet/oracle-and-adonet.md)
- [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
