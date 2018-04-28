Karakter tabanlı ile dizin oluşturma kullanarak <xref:System.Text.StringBuilder.Chars%2A> özelliği aşağıdaki koşullar altında çok yavaş olabilir:

- <xref:System.Text.StringBuilder> Örneğidir büyük (örneğin birkaç on binlerce karakterden oluşur).
- <xref:System.Text.StringBuilder> Olan "chunky." Diğer bir deyişle, yöntem çağrıları gibi yinelenen <xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType> nesnenin otomatik olarak genişlettikten <xref:System.Text.StringBuilder.Capacity%2A?displayProperty=nameWithType> özelliği ve ona bellek tahsis edilen yeni öbek.

Öbek halinde dizini oluşturmak için doğru arabellek bulmak için tüm bağlı listesini her karakter erişim anlatılmaktadır çünkü performans ciddi bir şekilde etkilenir.

> [!NOTE]
>  İçin bile büyük "chunky" <xref:System.Text.StringBuilder> nesnesi, kullanarak <xref:System.Text.StringBuilder.Chars%2A> dizin tabanlı erişim için aşağıdakilerden birini veya karakterden az sayıda özellik düşünülerek performans etkisi vardır; genellikle, bu bir **0(n)** işlemi. Önemli performans etkisi karakterleri yineleme oluşur <xref:System.Text.StringBuilder> nesne bir **O(n^2)** işlemi. 

Karakter tabanlı ile dizin oluşturma kullanırken performans sorunlarıyla karşılaşırsanız <xref:System.Text.StringBuilder> nesneleri, aşağıdaki geçici çözümlerden birini kullanabilirsiniz:

- Dönüştürme <xref:System.Text.StringBuilder> için örnek bir <xref:System.String> çağırarak <xref:System.Text.StringBuilder.ToString%2A> yöntemi, dizedeki karakter erişim.

- Var olan içeriğini kopyalayın <xref:System.Text.StringBuilder> yeni bir nesneye önceden boyutta <xref:System.Text.StringBuilder> nesnesi. Performansı artırır çünkü yeni <xref:System.Text.StringBuilder> nesnesi chunky değil. Örneğin:

   ```csharp
   // sbOriginal is the existing StringBuilder object
   var sbNew = new StringBuilder(sbOriginal.ToString(), sbOriginal.Length);
   ```
   ```vb
   ' sbOriginal is the existing StringBuilder object
   Dim sbNew = New StringBuilder(sbOriginal.ToString(), sbOriginal.Length)
   ```
- İlk kapasitesini ayarlama <xref:System.Text.StringBuilder> çağırarak yaklaşık olarak en fazla beklenen boyutuna eşit olan bir değer nesnesine <xref:System.Text.StringBuilder.%23ctor(System.Int32)> Oluşturucusu. Bu bellek olsa bile bloğunun tamamını ayırır Not <xref:System.Text.StringBuilder> nadiren kapasitesinin üst sınırına ulaştığında.
