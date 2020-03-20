---
title: Oracle için .NET Framework Veri Sağlayıcısı için Sistem Gereksinimleri
ms.date: 03/30/2017
ms.assetid: 054f76b9-1737-43f0-8160-84a00a387217
ms.openlocfilehash: dab3378d3022c01c674640201a67f3bdbb4f571f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174257"
---
# <a name="system-requirements-for-the-net-framework-data-provider-for-oracle"></a>Oracle için .NET Framework Veri Sağlayıcısı için Sistem Gereksinimleri

Oracle için .NET Framework Veri Sağlayıcısı, Microsoft Veri Erişim Bileşenleri (MDAC) sürüm 2.6 veya daha sonra gerektirir. MDAC 2.8 SP1 önerilir.  
  
 Ayrıca Oracle 8i Release 3 (8.1.7) Istemcisi veya daha sonra yüklü olmalıdır.  
  
 Oracle 9i sürümünden önceki Oracle Client yazılımı UTF16 veritabanlarına erişemez çünkü UTF16 Oracle 9i'de yeni bir özelliktir. Bu özelliği kullanmak için istemci yazılımınızı Oracle 9i veya daha sonrasına yükseltmeniz gerekir.  
  
## <a name="working-with-the-data-provider-for-oracle-and-unicode-data"></a>Oracle ve Unicode Data için Veri Sağlayıcısı ile çalışma  

Aşağıda, Oracle ve Oracle istemci kitaplıkları için .NET Framework Data Provider ile çalışırken göz önünde bulundurmanız gereken Unicode ile ilgili sorunların bir listesi verilmelidir. Daha fazla bilgi için Oracle belgelerinize bakın.  
  
### <a name="setting-the-unicode-value-in-a-connection-string-attribute"></a>Bağlantı Dize Özniteliğindeki Unicode Değerini Ayarlama  

Oracle ile çalışırken bağlantı dizeöz özniteliğini kullanabilirsiniz  
  
`Unicode=True`
  
UTF-16 modundaOracle istemci kitaplıklarını başlatma. Bu, Oracle istemci kitaplıklarının çok bayt dizeleri yerine UTF-16'yı (UCS-2'ye çok benzer) kabul etmesini neden olur. Bu, Oracle için Veri Sağlayıcısının ek çeviri çalışması olmadan her zaman herhangi bir Oracle kod sayfasıyla çalışmasını sağlar. Bu yapılandırma yalnızca, AL16UTF16'nın alternatif karakter kümesiyle oracle 9i veritabanıyla iletişim kurmak için Oracle 9i istemcilerini kullanıyorsanız çalışır. Bir Oracle 9i istemcisi bir Oracle 9i sunucusuyla iletişim kurduğunda, Unicode **CommandText** değerlerini Oracle9i sunucusunun kullandığı uygun çok bayt karakter kümesine dönüştürmek için ek kaynaklar gerekir. Bağlantı dizenize ekleyerek `Unicode=True` güvenli yapılandırmaya sahip olduğunuzu bildiğinizde bu durum önlenebilir.  
  
### <a name="mixing-versions-of-oracle-client-and-oracle-server"></a>Oracle Client ve Oracle Server'ın Karıştırma Sürümleri  

Sunucunun ulusal karakter kümesi AL16UTF16 (Oracle 9i için varsayılan ayar) olarak belirtildiğinde Oracle 9i veritabanlarında Oracle 9i veritabanlarında Oracle 8i istemcileri **NCHAR**, **NVARCHAR2**veya **NCLOB** verilerine erişemez. UTF-16 karakter seti desteği Oracle 9i'ye kadar kullanılmadığından, Oracle 8i istemcileri bunu okuyamaz.  
  
### <a name="working-with-utf-8-data"></a>UTF-8 Verileriyle Çalışma  

Alternatif karakter kümesini ayarlamak için, Kayıt Defteri AnahtarıHKEY_LOCAL_MACHINE\SOFTWARE\ORACLE\HOMEID\NLS_LANG'ı UTF8 olarak ayarlayın. Daha fazla bilgi için platformunuzdaki Oracle Yükleme notlarına bakın. Varsayılan ayar, Oracle Client yazılımını yüklediğiniz dilin birincil karakter kümesidir. Dilini bağlandığınız veritabanının ulusal dil karakter kümesiyle eşleşecek şekilde ayarlamamak, parametre ve sütun bağlamalarının ulusal karakter kümesine değil, birincil veritabanı karakter kümenizde veri göndermesine veya almasına neden olur.  
  
### <a name="oraclelob-can-only-update-full-characters"></a>OracleLob Yalnızca Tam Karakterleri Güncelleyebilir.  

Kullanılabilirlik nedenleriyle <xref:System.Data.OracleClient.OracleLob> nesne .NET Framework Stream sınıfından devralır ve **ReadByte** ve **WriteByte** yöntemlerini sağlar. Ayrıca, Oracle **LOB** nesnelerinin bölümleri üzerinde çalışan **CopyTo** ve **Erase**gibi yöntemleri de uygular. Buna karşılık, Oracle istemci yazılımı karakter **LOB**s **(CLOB** ve **NCLOB)** ile çalışmak için API'ler bir dizi sağlar. Ancak, bu API'ler yalnızca tam karakterler üzerinde çalışır. Bu fark nedeniyle, Oracle için Veri Sağlayıcısı, UTF-16 verileriyle bayt açısından çalışmak için **Read** ve **ReadByte** desteği uygular. Ancak, **OracleLob** nesnesinin diğer yöntemleri yalnızca tam karakter işlemlerine izin verir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Oracle ve ADO.NET](oracle-and-adonet.md)
- [ADO.NET’e Genel Bakış](ado-net-overview.md)
