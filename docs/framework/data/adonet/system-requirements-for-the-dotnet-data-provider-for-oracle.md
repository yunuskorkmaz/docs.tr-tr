---
title: Oracle için .NET Framework Veri Sağlayıcısı sistem gereksinimleri
ms.date: 03/30/2017
ms.assetid: 054f76b9-1737-43f0-8160-84a00a387217
ms.openlocfilehash: 664357fb08a6100b8b69d2b4e11edc77cdb81ac7
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833645"
---
# <a name="system-requirements-for-the-net-framework-data-provider-for-oracle"></a>Oracle için .NET Framework Veri Sağlayıcısı sistem gereksinimleri

Oracle için .NET Framework Veri Sağlayıcısı, Microsoft Data Access Components (MDAC) sürüm 2,6 veya üstünü gerektirir. MDAC 2,8 SP1 önerilir.  
  
 Ayrıca Oracle 8i Release 3 (8.1.7) Istemcisi veya sonraki bir sürümü yüklü olmalıdır.  
  
 Oracle 9i sürümünden önceki Oracle Istemci yazılımı, UTF16 veritabanlarına erişemiyor çünkü UTF16, Oracle 9i 'de yeni bir özelliktir. Bu özelliği kullanmak için, istemci yazılımınızı Oracle 9i veya sonraki bir sürüme yükseltmeniz gerekir.  
  
## <a name="working-with-the-data-provider-for-oracle-and-unicode-data"></a>Oracle ve Unicode verileri için Veri Sağlayıcısı çalışma  
 
Aşağıda, Oracle ve Oracle istemci kitaplıkları için .NET Framework Veri Sağlayıcısı çalışırken göz önünde bulundurmanız gereken Unicode ile ilgili sorunların bir listesi verilmiştir. Daha fazla bilgi için Oracle belgelerinize bakın.  
  
### <a name="setting-the-unicode-value-in-a-connection-string-attribute"></a>Bir bağlantı dizesi özniteliğinde Unicode değeri ayarlama  

Oracle ile çalışırken, bağlantı dizesi özniteliğini kullanabilirsiniz  
  
`Unicode=True`
  
Oracle istemci kitaplıklarını UTF-16 modunda başlatmak için. Bu, Oracle istemci kitaplıklarının çok baytlık dizeler yerine UTF-16 (UCS-2 ' ye çok benzer) kabul etmesine neden olur. Bu, Oracle 'ın Veri Sağlayıcısı ek çeviri olmadan her zaman herhangi bir Oracle kod sayfasıyla çalışmasını sağlar. Bu yapılandırma yalnızca, AL16UTF16 alternatif karakter kümesiyle bir Oracle 9i veritabanı ile iletişim kurmak için Oracle 9i istemcileri kullanıyorsanız geçerlidir. Bir Oracle 9i istemcisi bir Oracle 9i sunucusuyla iletişim kurduğunda, Unicode **CommandText** değerlerini Oracle9i sunucusunun kullandığı uygun çok baytlı karakter kümesine dönüştürmek için ek kaynaklar gerekir. Bağlantı dizenizi `Unicode=True` ekleyerek güvenli yapılandırmaya sahip olduğunuzu bildiğiniz durumlarda bu kaçınılabilir.  
  
### <a name="mixing-versions-of-oracle-client-and-oracle-server"></a>Oracle Istemcisi ve Oracle Server sürümlerini karıştırma  

Oracle 8i istemcileri, sunucu Ulusal karakter kümesi AL16UTF16 olarak belirtildiğinde (Oracle 9i için varsayılan ayar) Oracle 9i veritabanlarında **nchar**, **NVARCHAR2**veya **NCLOB** verilerine erişemez. UTF-16 karakter kümesi desteği Oracle 9i 'ye kadar tanıtılmadığından, Oracle 8ı istemcileri bunu okuyamıyorum.  
  
### <a name="working-with-utf-8-data"></a>UTF-8 verileriyle çalışma  

Alternatif karakter kümesini ayarlamak için, HKEY_LOCAL_MACHINE\SOFTWARE\ORACLE\HOMEID\NLS_LANG kayıt defteri anahtarını UTF8 olarak ayarlayın. Daha fazla bilgi için bkz. platformunuza Oracle yükleme notları. Varsayılan ayar, Oracle Istemci yazılımını yüklemekte olduğunuz dilin birincil karakter kümesidir. Dili bağlanmakta olduğunuz veritabanının ulusal dil karakter kümesiyle eşleşecek şekilde ayarlamama, parametre ve sütun bağlamalarının Ulusal karakter kümesine değil, birincil veritabanı karakter kümesine veri göndermesini veya almasına neden olur.  
  
### <a name="oraclelob-can-only-update-full-characters"></a>OracleLob yalnızca tam karakterleri güncelleştirebilir.  

Kullanılabilirlik nedenleriyle <xref:System.Data.OracleClient.OracleLob> nesnesi .NET Framework Stream sınıfından devralınır ve **ReadByte** ve **WriteByte** yöntemleri sağlar. Ayrıca, Oracle **lob** nesnelerinin bölümlerinde çalışan **CopyTo** ve **silme**gibi yöntemleri uygular. Buna karşılık, Oracle istemci yazılımı, **lob**'Lar (**CLOB** ve **NCLOB**) ile çalışmak için bir dizi API sağlar. Ancak, bu API 'Ler yalnızca tam karakterler üzerinde çalışır. Bu fark nedeniyle, Oracle 'ın Veri Sağlayıcısı, UTF-16 verileriyle bir bayt temelinde çalışacak şekilde **Read** ve **ReadByte** desteğini uygular. Ancak, **OracleLob** nesnesinin diğer yöntemleri yalnızca tam karakter işlemlerine izin verir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Oracle ve ADO.NET](oracle-and-adonet.md)
- [ADO.NET genel bakış](ado-net-overview.md)
