---
title: Bağlantı olayları
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5a29de74-acfc-4134-8616-829dd7ce0710
ms.openlocfilehash: 719e529c7813679f1e927b66e7db0e110714e438
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32758170"
---
# <a name="connection-events"></a>Bağlantı olayları
Tüm .NET Framework veri sağlayıcısı **bağlantı** bilgilendirici iletileri bir veri kaynağından veri almak veya belirlemek için kullanabileceğiniz iki olay nesneleriyle durumunu bir **bağlantı** sahip değiştirildi. Aşağıdaki tabloda olayların açıklanmaktadır **bağlantı** nesnesi.  
  
|Olay|Açıklama|  
|-----------|-----------------|  
|**InfoMessage**|Bir bilgi iletisidir bir veri kaynağından döndürülen oluşur. Bilgilendirici iletileri oluşturulan bir özel durum yol açmamasını iletileri bir veri kaynağından alınan ' dir.|  
|**StateChange**|Oluşur, durumu **bağlantı** değişiklikler.|  
  
## <a name="working-with-the-infomessage-event"></a>InfoMessage olayı ile çalışma  
 SQL Server veri kaynağı kullanarak bir, uyarılar ve bilgilendirici iletileri alabilirsiniz <xref:System.Data.SqlClient.SqlConnection.InfoMessage> olayı <xref:System.Data.SqlClient.SqlConnection> nesnesi. 16 11 önem düzeyine sahip veri kaynağından döndürülen hatalar bir özel durum oluşturulmasına neden. Ancak, <xref:System.Data.SqlClient.SqlConnection.InfoMessage> olay, bir hata ile ilişkili olmayan veri kaynağından alınan iletileri almak için kullanılabilir. Microsoft SQL Server, söz konusu olduğunda herhangi bir hata önem derecesi 10 veya daha az ileti bilgilendirme olarak değerlendirilir ve kullanılarak yakalanabilir <xref:System.Data.SqlClient.SqlConnection.InfoMessage> olay. Daha fazla bilgi için SQL Server Books Online'da "Hata iletisi önem düzeyleri" konusuna bakın.  
  
 <xref:System.Data.SqlClient.SqlConnection.InfoMessage> Olayı aldığı bir <xref:System.Data.SqlClient.SqlInfoMessageEventArgs> nesnesini içeren, buna onun **hataları** özelliği, veri kaynağından alınan iletileri koleksiyonu. Sorgulayabileceğiniz **hata** hatanın kaynağını yanı sıra, hata numarası ve ileti metni için bu koleksiyonundaki nesneleri. SQL Server için .NET Framework veri sağlayıcısı ayrıca veritabanı, saklı yordam ve iletinin geldiği satır numarası hakkında ayrıntılı bilgi içerir.  
  
### <a name="example"></a>Örnek  
 Aşağıdaki kod örneği için bir olay işleyicisi ekleme gösterir <xref:System.Data.SqlClient.SqlConnection.InfoMessage> olay.  
  
```vb  
' Assumes that connection represents a SqlConnection object.  
  AddHandler connection.InfoMessage, _  
    New SqlInfoMessageEventHandler(AddressOf OnInfoMessage)  
  
Private Shared Sub OnInfoMessage(sender As Object, _  
  args As SqlInfoMessageEventArgs)  
  Dim err As SqlError  
  For Each err In args.Errors  
    Console.WriteLine("The {0} has received a severity {1}, _  
       state {2} error number {3}\n" & _  
      "on line {4} of procedure {5} on server {6}:\n{7}", _  
      err.Source, err.Class, err.State, err.Number, err.LineNumber, _  
    err.Procedure, err.Server, err.Message)  
  Next  
End Sub  
```  
  
```csharp  
// Assumes that connection represents a SqlConnection object.  
  connection.InfoMessage +=   
    new SqlInfoMessageEventHandler(OnInfoMessage);  
  
protected static void OnInfoMessage(  
  object sender, SqlInfoMessageEventArgs args)  
{  
  foreach (SqlError err in args.Errors)  
  {  
    Console.WriteLine(  
  "The {0} has received a severity {1}, state {2} error number {3}\n" +  
  "on line {4} of procedure {5} on server {6}:\n{7}",  
   err.Source, err.Class, err.State, err.Number, err.LineNumber,   
   err.Procedure, err.Server, err.Message);  
  }  
}  
```  
  
## <a name="handling-errors-as-infomessages"></a>InfoMessages hataları işleme  
 <xref:System.Data.SqlClient.SqlConnection.InfoMessage> Olay normalde sunucudan gönderilen bilgi ve uyarı iletileri için kov. Ancak, gerçek bir hata oluştuğunda, yürütülmesi **ExecuteNonQuery** veya **ExecuteReader** sunucu işlemi başlatan yöntem durdurulamaz ve bir özel durum.  
  
 Devam etmek istiyorsanız hataları bağımsız olarak bir komut deyimlerinde kalan işleme sunucu tarafından üretilen, Ayarla <xref:System.Data.SqlClient.SqlConnection.FireInfoMessageEventOnUserErrors%2A> özelliği <xref:System.Data.SqlClient.SqlConnection> için `true`. Bunun yapılması neden tetiklenecek bağlantı <xref:System.Data.SqlClient.SqlConnection.InfoMessage> bir özel durum atma ve işleme kesintiye yerine hataları için olay. İstemci uygulaması bu olayı işlemek ve hata koşullarını yanıt.  
  
> [!NOTE]
>  Komut işlemeyi durdur sunucuya neden olan hata 17 veya üstü önem düzeyine sahip bir özel durum olarak ele alınması gerekir. Bir özel nasıl hata olarak ele alınır bağımsız olarak bu durumda, durum <xref:System.Data.SqlClient.SqlConnection.InfoMessage> olay.  
  
## <a name="working-with-the-statechange-event"></a>StateChange olay ile çalışma  
 **StateChange** olayı oluşur, durumu bir **bağlantı** değişiklikler. **StateChange** olayı aldığı <xref:System.Data.StateChangeEventArgs> durumundaki değişikliği belirlemek etkinleştirme **bağlantı** kullanarak **OriginalState** ve **CurrentState** özellikleri. **OriginalState** özelliği bir <xref:System.Data.ConnectionState> durumunu belirten numaralandırma **bağlantı** önce onu değiştirildi. **CurrentState** olan bir <xref:System.Data.ConnectionState> durumunu belirten numaralandırma **bağlantı** onu değiştikten sonra.  
  
 Aşağıdaki kod örneğinde **StateChange** konsoluna bir ileti yazmak için olay zaman durumunu **bağlantı** değişiklikler.  
  
```vb  
' Assumes connection represents a SqlConnection object.  
  AddHandler connection.StateChange, _  
    New StateChangeEventHandler(AddressOf OnStateChange)  
  
Protected Shared Sub OnStateChange( _  
  sender As Object, args As StateChangeEventArgs)  
  
  Console.WriteLine( _  
  "The current Connection state has changed from {0} to {1}.", _  
  args.OriginalState, args.CurrentState)  
End Sub  
```  
  
```csharp  
// Assumes connection represents a SqlConnection object.  
  connection.StateChange  += new StateChangeEventHandler(OnStateChange);  
  
protected static void OnStateChange(object sender,   
  StateChangeEventArgs args)  
{  
  Console.WriteLine(  
    "The current Connection state has changed from {0} to {1}.",  
      args.OriginalState, args.CurrentState);  
}  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri Kaynağına Bağlanma](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
