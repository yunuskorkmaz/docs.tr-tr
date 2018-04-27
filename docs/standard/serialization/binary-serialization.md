---
title: İkili seri hale getirme
ms.date: 01/02/2018
ms.prod: .net
ms.topic: article
helpviewer_keywords:
- binary serialization
- serialization, about serialization
- deserialization
- binary serialization, about serialization
- binary serialization, .net core serialization
- serialization, cross-framework
ms.assetid: 2b1ea3be-1152-4032-b2b3-07794054c405
caps.latest.revision: 5
author: ViktorHofer
ms.author: mairaw
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: af63ca4716a92c8fb3eb05d9addda466dbb04a4e
ms.sourcegitcommit: 68b60d38043e50104ccc90c76f8599b1ffe18346
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2018
---
# <a name="binary-serialization"></a>İkili seri hale getirme

Serileştirme depolama ortamına bir nesne durumunu depolama işlemi olarak tanımlanabilir. Bu işlem sırasında nesnenin genel ve özel alanlar ve sınıfı içeren derlemenin dahil olmak üzere bu sınıfın adını ardından bir veri akışına yazılan bayt akışı dönüştürülür. Nesnenin seri durumdan daha sonra orijinal nesneyi tam bir kopyası oluşturulur.

Seri hale getirme mekanizmasını nesne yönelimli bir ortamda uygularken, kullanım kolaylığı ve esnekliği arasında bileşim sayısı yapmanız gerekir. İşlemin büyük ölçüde otomatik, sağlanan işlem üzerinde yeterli denetim verilir. Örneğin, burada basit ikili serileştirme yeterli değil veya bir sınıf hangi alanları seri hale gerek karar vermek için belirli bir neden olabilir durumlarda gerçekleşebilir. Aşağıdaki bölümlerde .NET ile birlikte sağlanan sağlam seri hale getirme mekanizmasını inceleyin ve bir dizi gereksinimlerinizi karşılamak için işlem özelleştirmenizi önemli özellik vurgulayın.

> [!NOTE]
> Nesnenin serileştirildiği ve farklı .NET Framework sürümleri kullanılarak seri durumdan UTF-8 veya UTF-7 kodlanmış nesne durumunu korunur değil.

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]

İkili seri hale getirme yapısını özel üyeleri bir nesne ve bu nedenle durumunu değiştirme içinde değiştirilmesine izin verdiği ölçüde ortak API yüzeyi üzerinde çalışan diğer serileştirme çerçeveler JSON.NET gibi önerilir.

## <a name="binary-serialization-in-net-core"></a>.NET Core ikili seri hale getirme

.NET core türlerinin bir kümeyle ikili serileştirme destekler. Desteklenen türlerden birinde listesini görebilir [seri hale getirilebilir türler bölüm](#serializable-types). Türleri tanımlı kümesi .NET Framework 4.5.1 ve sonraki sürümleri ve .NET Core 2.0 ve sonraki sürümler arasında seri hale getirilebilir olması garanti edilir. Mono gibi diğer .NET uygulamaları resmi olarak desteklenmez, ancak aynı zamanda çalışan.

### <a name="serializable-types"></a>Seri hale getirilebilir türler

- <xref:Microsoft.CSharp.RuntimeBinder.RuntimeBinderException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:Microsoft.CSharp.RuntimeBinder.RuntimeBinderInternalCompilerException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.AccessViolationException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.AggregateException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.AppDomainUnloadedException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.ApplicationException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.ArgumentException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.ArgumentNullException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.ArgumentOutOfRangeException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.ArithmeticException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.Array?displayProperty=nameWithType>   
- <xref:System.ArraySegment%601?displayProperty=nameWithType>   
- <xref:System.ArrayTypeMismatchException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.Attribute?displayProperty=nameWithType>
- <xref:System.BadImageFormatException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.Boolean?displayProperty=nameWithType>   
- <xref:System.Byte?displayProperty=nameWithType>   
- <xref:System.CannotUnloadAppDomainException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.Char?displayProperty=nameWithType>   
- <xref:System.Collections.ArrayList?displayProperty=nameWithType>   
- <xref:System.Collections.BitArray?displayProperty=nameWithType>   
- <xref:System.Collections.Comparer?displayProperty=nameWithType>   
- <xref:System.Collections.DictionaryEntry?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.Comparer%601?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.EqualityComparer%601?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.HashSet%601?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.KeyNotFoundException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.Collections.Generic.KeyValuePair%602?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.LinkedList%601?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.SortedDictionary%602?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.SortedList%602?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.SortedSet%601?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.Stack%601?displayProperty=nameWithType>   
- <xref:System.Collections.Hashtable?displayProperty=nameWithType>   
- <xref:System.Collections.ObjectModel.Collection%601?displayProperty=nameWithType>   
- <xref:System.Collections.ObjectModel.KeyedCollection%602?displayProperty=nameWithType>   
- <xref:System.Collections.ObjectModel.ObservableCollection%601?displayProperty=nameWithType>   
- <xref:System.Collections.ObjectModel.ReadOnlyCollection%601?displayProperty=nameWithType>   
- <xref:System.Collections.ObjectModel.ReadOnlyDictionary%602?displayProperty=nameWithType>   
- <xref:System.Collections.ObjectModel.ReadOnlyObservableCollection%601?displayProperty=nameWithType>   
- <xref:System.Collections.Queue?displayProperty=nameWithType>   
- <xref:System.Collections.SortedList?displayProperty=nameWithType>   
- <xref:System.Collections.Specialized.HybridDictionary?displayProperty=nameWithType>   
- <xref:System.Collections.Specialized.ListDictionary?displayProperty=nameWithType>   
- <xref:System.Collections.Specialized.OrderedDictionary?displayProperty=nameWithType>   
- <xref:System.Collections.Specialized.StringCollection?displayProperty=nameWithType>   
- <xref:System.Collections.Specialized.StringDictionary?displayProperty=nameWithType>   
- <xref:System.Collections.Stack?displayProperty=nameWithType>   
- `System.Collections.Generic.NonRandomizedStringEqualityComparer` <!--zz <xref:System.Collections.Generic.NonRandomizedStringEqualityComparer?displayProperty=nameWithType> --> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.ComponentModel.BindingList%601?displayProperty=nameWithType>   
- <xref:System.ComponentModel.DataAnnotations.ValidationException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.ComponentModel.Design.CheckoutException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.ComponentModel.InvalidAsynchronousStateException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.ComponentModel.InvalidEnumArgumentException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.ComponentModel.LicenseException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir, .NET Framework serileştirmeyle .NET Core desteklenmez)
- <xref:System.ComponentModel.WarningException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.ComponentModel.Win32Exception?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.Configuration.ConfigurationErrorsException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.Configuration.ConfigurationException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.Configuration.Provider.ProviderException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.Configuration.SettingsPropertyIsReadOnlyException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.Configuration.SettingsPropertyNotFoundException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.Configuration.SettingsPropertyWrongTypeException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.ContextMarshalException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.DBNull?displayProperty=nameWithType> (.NET Core 2.0.2 ve sonraki sürümlerde kullanılabilir)   
- <xref:System.Data.Common.DbException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.Data.ConstraintException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.Data.DBConcurrencyException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.Data.DataException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.Data.DataSet?displayProperty=nameWithType>
- <xref:System.Data.DataTable?displayProperty=nameWithType> (SerializationFormat.Binary için RemotingFormat ayarlanmadığı sürece; bu durumda, yalnızca .NET çekirdeği 2.1 ve sonraki sürümler ile değiştirilebilmesi için.)   
- <xref:System.Data.DeletedRowInaccessibleException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.Data.DuplicateNameException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.Data.EvaluateException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.Data.InRowChangingEventException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.Data.InvalidConstraintException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.Data.InvalidExpressionException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.Data.MissingPrimaryKeyException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.Data.NoNullAllowedException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.Data.Odbc.OdbcException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.Data.OperationAbortedException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.Data.PropertyCollection?displayProperty=nameWithType>   
- <xref:System.Data.ReadOnlyException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.Data.RowNotInTableException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.Data.SqlClient.SqlException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir, .NET Framework serileştirmeyle .NET Core desteklenmez)
- <xref:System.Data.SqlTypes.SqlAlreadyFilledException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.Data.SqlTypes.SqlBoolean?displayProperty=nameWithType>   
- <xref:System.Data.SqlTypes.SqlByte?displayProperty=nameWithType>   
- <xref:System.Data.SqlTypes.SqlDateTime?displayProperty=nameWithType>   
- <xref:System.Data.SqlTypes.SqlDouble?displayProperty=nameWithType>   
- <xref:System.Data.SqlTypes.SqlGuid?displayProperty=nameWithType>   
- <xref:System.Data.SqlTypes.SqlInt16?displayProperty=nameWithType>   
- <xref:System.Data.SqlTypes.SqlInt32?displayProperty=nameWithType>   
- <xref:System.Data.SqlTypes.SqlInt64?displayProperty=nameWithType>   
- <xref:System.Data.SqlTypes.SqlNotFilledException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.Data.SqlTypes.SqlNullValueException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.Data.SqlTypes.SqlString?displayProperty=nameWithType>   
- <xref:System.Data.SqlTypes.SqlTruncateException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.Data.SqlTypes.SqlTypeException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.Data.StrongTypingException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.Data.SyntaxErrorException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.Data.VersionNotFoundException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.DataMisalignedException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.DateTime?displayProperty=nameWithType>   
- <xref:System.DateTimeOffset?displayProperty=nameWithType>   
- <xref:System.Decimal?displayProperty=nameWithType>   
- `System.Diagnostics.Contracts.ContractException` <!--zz <xref:System.Diagnostics.Contracts.ContractException?displayProperty=nameWithType> --> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.Diagnostics.Tracing.EventSourceException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.IO.DirectoryNotFoundException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.DirectoryServices.AccountManagement.MultipleMatchesException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.DirectoryServices.AccountManagement.NoMatchingPrincipalException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.DirectoryServices.AccountManagement.PasswordException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.DirectoryServices.AccountManagement.PrincipalException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.DirectoryServices.AccountManagement.PrincipalExistsException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.DirectoryServices.AccountManagement.PrincipalOperationException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.DirectoryServices.AccountManagement.PrincipalServerDownException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.DirectoryServices.ActiveDirectory.ActiveDirectoryObjectExistsException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.DirectoryServices.ActiveDirectory.ActiveDirectoryObjectNotFoundException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.DirectoryServices.ActiveDirectory.ActiveDirectoryOperationException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.DirectoryServices.ActiveDirectory.ActiveDirectoryServerDownException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.DirectoryServices.ActiveDirectory.ForestTrustCollisionException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.DirectoryServices.ActiveDirectory.SyncFromAllServersOperationException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.DirectoryServices.DirectoryServicesCOMException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.DirectoryServices.Protocols.BerConversionException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.DirectoryServices.Protocols.DirectoryException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.DirectoryServices.Protocols.DirectoryOperationException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.DirectoryServices.Protocols.LdapException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.DirectoryServices.Protocols.TlsOperationException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.DivideByZeroException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.DllNotFoundException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.Double?displayProperty=nameWithType>   
- <xref:System.Drawing.Color?displayProperty=nameWithType>   
- <xref:System.Drawing.Point?displayProperty=nameWithType>   
- <xref:System.Drawing.PointF?displayProperty=nameWithType>   
- <xref:System.Drawing.Rectangle?displayProperty=nameWithType>   
- <xref:System.Drawing.RectangleF?displayProperty=nameWithType>   
- <xref:System.Drawing.Size?displayProperty=nameWithType>   
- <xref:System.Drawing.SizeF?displayProperty=nameWithType>   
- <xref:System.DuplicateWaitObjectException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.EntryPointNotFoundException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.Enum?displayProperty=nameWithType>   
- <xref:System.EventArgs?displayProperty=nameWithType> (.NET Core 2.0.6 ve sonraki sürümlerde kullanılabilir)
- <xref:System.Exception?displayProperty=nameWithType>   
- <xref:System.ExecutionEngineException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.FieldAccessException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.FormatException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.Globalization.CompareInfo?displayProperty=nameWithType>   
- <xref:System.Globalization.CultureNotFoundException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.Globalization.SortVersion?displayProperty=nameWithType>   
- <xref:System.Guid?displayProperty=nameWithType>   
- `System.IO.Compression.ZLibException` <!--zz <xref:System.IO.Compression.ZLibException?displayProperty=nameWithType --> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.IO.DriveNotFoundException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.IO.EndOfStreamException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.IO.FileFormatException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.IO.FileLoadException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.IO.FileNotFoundException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.IO.IOException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.IO.InternalBufferOverflowException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.IO.InvalidDataException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.IO.IsolatedStorage.IsolatedStorageException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.IO.PathTooLongException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.IndexOutOfRangeException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.InsufficientExecutionStackException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.InsufficientMemoryException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.Int16?displayProperty=nameWithType>   
- <xref:System.Int32?displayProperty=nameWithType>   
- <xref:System.Int64?displayProperty=nameWithType>   
- <xref:System.IntPtr?displayProperty=nameWithType>   
- <xref:System.InvalidCastException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.InvalidOperationException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.InvalidProgramException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.InvalidTimeZoneException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.MemberAccessException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.MethodAccessException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.MissingFieldException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.MissingMemberException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.MissingMethodException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.MulticastNotSupportedException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.Net.Cookie?displayProperty=nameWithType>   
- <xref:System.Net.CookieCollection?displayProperty=nameWithType>   
- <xref:System.Net.CookieContainer?displayProperty=nameWithType>   
- <xref:System.Net.CookieException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.Net.HttpListenerException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.Net.Mail.SmtpException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.Net.Mail.SmtpFailedRecipientException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.Net.Mail.SmtpFailedRecipientsException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.Net.NetworkInformation.NetworkInformationException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.Net.NetworkInformation.PingException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.Net.ProtocolViolationException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.Net.Sockets.SocketException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.Net.WebException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.Net.WebSockets.WebSocketException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.NotFiniteNumberException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.NotImplementedException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.NotSupportedException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.NullReferenceException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.Nullable%601?displayProperty=nameWithType>   
- <xref:System.Numerics.BigInteger?displayProperty=nameWithType>   
- <xref:System.Numerics.Complex?displayProperty=nameWithType>   
- <xref:System.Object?displayProperty=nameWithType>   
- <xref:System.ObjectDisposedException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.OperationCanceledException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.OutOfMemoryException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.OverflowException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.PlatformNotSupportedException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.RankException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.Reflection.AmbiguousMatchException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.Reflection.CustomAttributeFormatException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.Reflection.InvalidFilterCriteriaException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.Reflection.ReflectionTypeLoadException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir, .NET Framework serileştirmeyle .NET Core desteklenmez)
- <xref:System.Reflection.TargetException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.Reflection.TargetInvocationException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.Reflection.TargetParameterCountException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.Resources.MissingManifestResourceException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.Resources.MissingSatelliteAssemblyException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.Runtime.CompilerServices.RuntimeWrappedException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.Runtime.InteropServices.COMException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.Runtime.InteropServices.ExternalException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.Runtime.InteropServices.InvalidComObjectException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.Runtime.InteropServices.InvalidOleVariantTypeException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.Runtime.InteropServices.MarshalDirectiveException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.Runtime.InteropServices.SEHException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.Runtime.InteropServices.SafeArrayRankMismatchException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.Runtime.InteropServices.SafeArrayTypeMismatchException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.Runtime.Serialization.InvalidDataContractException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.Runtime.Serialization.SerializationException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.SByte?displayProperty=nameWithType>   
- <xref:System.Security.AccessControl.PrivilegeNotHeldException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.Security.Authentication.AuthenticationException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.Security.Authentication.InvalidCredentialException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.Security.Cryptography.CryptographicException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.Security.Cryptography.CryptographicUnexpectedOperationException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- `System.Security.Cryptography.Xml.CryptoSignedXmlRecursionException` <!--zz <xref:System.Security.Cryptography.Xml.CryptoSignedXmlRecursionException?displayProperty=nameWithType --> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.Security.HostProtectionException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.Security.Policy.PolicyException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.Security.Principal.IdentityNotMappedException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.Security.SecurityException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerinde, sınırlı serileştirme verileri kullanılabilir)
- <xref:System.Security.VerificationException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.Security.XmlSyntaxException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.ServiceProcess.TimeoutException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.Single?displayProperty=nameWithType>   
- <xref:System.StackOverflowException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.String?displayProperty=nameWithType>   
- <xref:System.StringComparer?displayProperty=nameWithType>   
- <xref:System.SystemException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.Text.DecoderFallbackException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.Text.EncoderFallbackException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.Text.RegularExpressions.RegexMatchTimeoutException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.Text.StringBuilder?displayProperty=nameWithType>   
- <xref:System.Threading.AbandonedMutexException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.Threading.BarrierPostPhaseException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.Threading.LockRecursionException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.Threading.SemaphoreFullException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.Threading.SynchronizationLockException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.Threading.Tasks.TaskCanceledException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.Threading.Tasks.TaskSchedulerException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.Threading.ThreadAbortException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.Threading.ThreadInterruptedException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.Threading.ThreadStartException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.Threading.ThreadStateException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.Threading.WaitHandleCannotBeOpenedException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.TimeSpan?displayProperty=nameWithType>   
- <xref:System.TimeZoneInfo.AdjustmentRule?displayProperty=nameWithType>   
- <xref:System.TimeZoneInfo?displayProperty=nameWithType>   
- <xref:System.TimeZoneNotFoundException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.TimeoutException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.Transactions.TransactionAbortedException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.Transactions.TransactionException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.Transactions.TransactionInDoubtException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.Transactions.TransactionManagerCommunicationException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.Transactions.TransactionPromotionException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.Tuple?displayProperty=nameWithType>   
- <xref:System.TypeAccessException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.TypeInitializationException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.TypeLoadException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.TypeUnloadedException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.UInt16?displayProperty=nameWithType>   
- <xref:System.UInt32?displayProperty=nameWithType>   
- <xref:System.UInt64?displayProperty=nameWithType>   
- <xref:System.UIntPtr?displayProperty=nameWithType>   
- <xref:System.UnauthorizedAccessException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.Uri?displayProperty=nameWithType>   
- <xref:System.UriFormatException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.ValueTuple?displayProperty=nameWithType> (.NET Framework 4.7 ve önceki sürümlerde getirilemez)  
- <xref:System.ValueType?displayProperty=nameWithType>   
- <xref:System.Version?displayProperty=nameWithType>   
- <xref:System.WeakReference%601?displayProperty=nameWithType>   
- <xref:System.WeakReference?displayProperty=nameWithType>   
- <xref:System.Xml.Schema.XmlSchemaException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.Xml.Schema.XmlSchemaInferenceException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.Xml.Schema.XmlSchemaValidationException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.Xml.XPath.XPathException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.Xml.XmlException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.Xml.Xsl.XsltCompileException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)
- <xref:System.Xml.Xsl.XsltException?displayProperty=nameWithType> (.NET Core 2.0.4 ve sonraki sürümlerde kullanılabilir)

## <a name="in-this-section"></a>Bu bölümde

 [Serileştirme Kavramları](../../../docs/standard/serialization/serialization-concepts.md)  
 Serileştirme olduğu yararlı iki kullanıldığı senaryoları tartışır: zaman kalıcı veri depolama ve geçerken nesneleri uygulama etki alanlarında.  
  
 [Temel Serileştirme](../../../docs/standard/serialization/basic-serialization.md)  
 İkili kullanın ve nesneleri serileştirmek için biçimlendiricileri SOAP açıklar.  
  
 [Seçmeli Serileştirme](../../../docs/standard/serialization/selective-serialization.md)  
 Serileştirilmiş öğesinden bir sınıf bazı üyeler önlemek nasıl açıklar.  
  
 [Özel Serileştirme](../../../docs/standard/serialization/custom-serialization.md)  
 Kullanarak bir sınıf için serileştirme özelleştirmeyi açıklar <xref:System.Runtime.Serialization.ISerializable> arabirimi.  
  
 [Serileştirme İşlemi Adımları](../../../docs/standard/serialization/steps-in-the-serialization-process.md)  
 Kurs açıklayan eylemi serileştirme ne zaman alan <xref:System.Runtime.Serialization.Formatter.Serialize%2A> yöntemi, bir biçimlendirici üzerinde çağrılır.  
  
 [Sürüme Dayanıklı Serileştirme](../../../docs/standard/serialization/version-tolerant-serialization.md)  
 Özel durumlar oluşturan uygulamaların neden olmadan zaman içinde değiştirilebilir serializable türler nasıl oluşturulacağını açıklar.  
  
 [Serileştirme Yönergeleri](../../../docs/standard/serialization/serialization-guidelines.md)  
 Bir nesneyi serileştirmek ne zaman karar için bazı genel yönergeleri sağlar.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.Runtime.Serialization>  
 Serileştirme ve seri kaldırma nesneler için kullanılan sınıfları içerir.  
  
## <a name="related-sections"></a>İlgili bölümler  
 [XML ve SOAP Serileştirme](../../../docs/standard/serialization/xml-and-soap-serialization.md)  
 Ortak dil çalışma zamanı ile içerdiği XML serileştirme mekanizması açıklanmaktadır.  
  
 [Güvenlik ve Serileştirme](../../../docs/framework/misc/security-and-serialization.md)  
 Serileştirme gerçekleştiren kod yazarken izlemek için güvenli kodlama yönergeleri açıklar.  
  
 [Uzak nesneleri](https://msdn.microsoft.com/library/515686e6-0a8d-42f7-8188-73abede57c58)  
 Çeşitli iletişimleri .NET Framework için kullanılabilecek yöntemleri Uzaktan iletişimler açıklar.  
  
 [ASP.NET ve XML Web hizmeti istemcileri kullanılarak oluşturulan XML Web Hizmetleri](https://msdn.microsoft.com/library/1e64af78-d705-4384-b08d-591a45f4379c)  
 Açıklayan ve ASP.NET kullanılarak oluşturulan XML Web Hizmetleri program açıklayan konuları sağlar.
